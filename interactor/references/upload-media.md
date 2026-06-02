# Uploading Media

You can upload media in two ways:

- Public url. Platform will download and host the image.
- For local images: encode base64 media in the url. If you need to upload a lot of large images, you can split it on several patches

There is no separate endpoint to upload an image, so you must do it via patch schema as described above.
