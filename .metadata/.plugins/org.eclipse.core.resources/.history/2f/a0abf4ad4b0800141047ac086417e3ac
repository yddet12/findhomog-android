package org.opencv.samples.facedetect;

import org.opencv.core.Mat;
import org.opencv.core.MatOfRect;

public class NativeCodeInterface
{
    /*Constructor, called on startup "Part One"*/
    public NativeCodeInterface(String haarfile, String idfile) {
        mNativeObj = nativeCreateObject(haarfile, idfile);
    }

  
    public void setMinFaceSize(int size) {
        //nativeSetFaceSize(mNativeObj, size);
    }
   
    /*Loop, called with onCameraFrame "Part Two"*/
    public void nativeLoopInterface(Mat imageGray, MatOfRect faces) {
        nativeLoop(mNativeObj, imageGray.getNativeObjAddr(), faces.getNativeObjAddr());
    }

    public void release() {
        //nativeDestroyObject(mNativeObj);
        //mNativeObj = 0;
    }
    public void start() {
        //nativeStart(mNativeObj);
    }

    public void stop() {
        //nativeStop(mNativeObj);
    }

    private long mNativeObj = 0;

    private static native long nativeCreateObject(String haarfile, String identityfile);
    private static native void nativeDestroyObject(long thiz);
    private static native void nativeStart(long thiz);
    private static native void nativeStop(long thiz);
    private static native void nativeLoop(long mac, long inputImage, long faces);
}