## Android TextureView
### SurfaceView的特点
①：运行在独立的窗口（surface），绘制效率高。

②：不能使用普通View的api（如平移、旋转、缩放或设置透明度等），也难以放在ListView或ScrollView中
### TextureView的特点
①：与SurfaceView一样在子线程中绘制。

②：没有运行在独立的surface中，因此可以运用普通View的api，必须在硬件加速开启的窗口中。

③：TextureView比SurfaceView更耗内存，而且可能会有1～3帧的延迟

    mTexture = (TextureView) findViewById(R.id.textureView);
	mTexture.setSurfaceTextureListener(new TextureView.SurfaceTextureListener() {
	    @Override
	    public void onSurfaceTextureAvailable(SurfaceTexture surface, int width, int height) {
			//在SurfaceTexture准备使用时调用
	    }

	    @Override
	    public void onSurfaceTextureSizeChanged(SurfaceTexture surface, int width, int height) {
			//当SurfaceTexture缓冲区大小更改时调用
	    }

	    @Override
	    public boolean onSurfaceTextureDestroyed(SurfaceTexture surface) {
			//当指定SurfaceTexture即将被销毁时调用。
			//如果返回true，则调用此方法后，表面纹理中不会发生渲染。
			//如果返回false，则客户端需要调用release()。大多数应用程序应该返回true
	        return false;
	    }

	    @Override
	    public void onSurfaceTextureUpdated(SurfaceTexture surface) {
			//当指定SurfaceTexture的更新时调用updateTexImage()
	    }
	});