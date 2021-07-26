Get image from url

```C#

ServicePointManager.SecurityProtocol = (SecurityProtocolType)3072; // if you get security error, you can add this statement
WebRequest request = WebRequest.Create(imagePath); //imagePath is Url
WebResponse response = request.GetResponse();
Stream stream = response.GetResponseStream();
Image img = Image.FromStream(stream);
response.Close();


```

Compress quality

```C#
ImageCodecInfo[] encoders = ImageCodecInfo.GetImageEncoders();
ImageCodecInfo jpegEncoder = null;
for (int x = 0; x < encoders.Length; x++)
{
    if (string.Compare(encoders[x].MimeType, "image/jpeg", true) == 0)
    {
        jpegEncoder = encoders[x];
        break;
    }
}
if (jpegEncoder == null) throw new ApplicationException("Could not find JPEG encoder!");
EncoderParameters prms = new EncoderParameters(1);
prms.Param[0] = new EncoderParameter(System.Drawing.Imaging.Encoder.Quality, 60L); //60L mean the quality. value should be 0 to 																					 100.100 mean high quality

//save image
//you can resize image here
img.Save(targetThumPath, jpegEncoder, prms);//targetThumPath is the path you want to save
img.Dispose(); 


//other method
private static ImageCodecInfo GetEncoder(ImageFormat format)
{
    ImageCodecInfo[] codecs = ImageCodecInfo.GetImageDecoders();
    foreach (ImageCodecInfo codec in codecs)
    {
        if (codec.FormatID == format.Guid)
        {
            return codec;
        }
    }
    return null;
}
//save image
//you can resize image here
ImageCodecInfo jpgEncoder = GetEncoder(ImageFormat.Jpeg)
img.Save(targetThumPath,jpgEncoder, prms);
thumbnail.Dispose(); 
```

Resize Image

```C#
public static Bitmap ResizeImage(Image image, int width, int height)
{
    var destRect = new Rectangle(0, 0, width, height);
    var destImage = new Bitmap(width, height);

    destImage.SetResolution(image.HorizontalResolution, image.VerticalResolution);

    using (var graphics = Graphics.FromImage(destImage))
    {
        graphics.CompositingMode = CompositingMode.SourceCopy;
        graphics.CompositingQuality = CompositingQuality.HighQuality;
        graphics.InterpolationMode = InterpolationMode.HighQualityBicubic;
        graphics.SmoothingMode = SmoothingMode.HighQuality;
        graphics.PixelOffsetMode = PixelOffsetMode.HighQuality;

        using (var wrapMode = new ImageAttributes())
        {
            wrapMode.SetWrapMode(WrapMode.TileFlipXY);                                                              
            graphics.DrawImage(image, destRect, 0, 0, image.Width, image.Height, GraphicsUnit.Pixel, wrapMode);
        }
    }

    return destImage;
}
```

