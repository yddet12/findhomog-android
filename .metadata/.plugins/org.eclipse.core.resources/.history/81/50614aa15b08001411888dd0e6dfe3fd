#include <NativeCodeInterface_jni.h>
#include <opencv2/core/core.hpp>
#include <opencv2/contrib/detection_based_tracker.hpp>
#include "opencv2/highgui/highgui.hpp"
#include "opencv2/contrib/contrib.hpp"

#include <string>
#include <vector>

#include <android/log.h>

#define LOG_TAG "FaceDetection/DetectionBasedTracker"
#define LOGD(...) ((void)__android_log_print(ANDROID_LOG_DEBUG, LOG_TAG, __VA_ARGS__))

using namespace std;
using namespace cv;

// This is the datatype that the PrepareFiles function will return
// PrepareFiles loads csv file, training images, and haar cascade file
struct modelandcascade {
   Ptr<FaceRecognizer> themodel;
   CascadeClassifier thecc;
   int w,h;
};

inline void vector_Rect_to_Mat(vector<Rect>& v_rect, Mat& mat)
{
    mat = Mat(v_rect, true);
}// This is the datatype that the PrepareFiles function will return
// PrepareFiles loads csv file, training images, and haar cascade file


JNIEXPORT jlong JNICALL Java_org_opencv_samples_facedetect_NativeCodeInterface_nativeCreateObject
(JNIEnv * jenv, jclass, jstring jhaarfile, jstring jidentityfile)
{
    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeCreateObject enter");
    const char* jhaarstr = jenv->GetStringUTFChars(jhaarfile, NULL);
    string haarFileName(jhaarstr);

    const char* jidentitystr = jenv->GetStringUTFChars(jidentityfile, NULL);
        //string identityFileName(jhaarstr); // deleted 2:17pm on 7/9; replaced with the below line (ie replaced jhaarstr with jidentitystr)
        string identityFileName(jidentitystr);

    jlong result = 0;

    try
    {
        //PREPARE MODELS
        modelandcascade * datatoreturn = new modelandcascade();
        vector<Mat> images; // holds all the training images
        vector<int> labels; // holds the labels (1 for person#1, etc) corresponding to each image in images

        // Load the cascade-classifier file
        datatoreturn->thecc.load(haarFileName);

        //cout << "loading model" << endl;
        datatoreturn->themodel = createLBPHFaceRecognizer();
        datatoreturn->themodel->load(identityFileName);
        LOGD("passed loading the model");
        //got to here
        std::string str;
        LOGD("passed right before getstring");
        //got to here
        //datatoreturn->themodel->getString(str);

        //LOGD("passed datatoreturn->themodel %s",str.c_str());
        //cout << "loading dimensions" << endl;
        //ifstream dimin;
        //dimin.open("dims.txt");
        //string wstring, hstring;
        //getline(dimin, wstring);
        //getline(dimin, hstring);

        datatoreturn->w = 274;//atoi(wstring.c_str());
        datatoreturn->h = 274;//atoi(hstring.c_str());
        LOGD("passed loading w and h");
        //made it to here
        return (jlong)datatoreturn;
        //END PREPARE MODELS
    }
    catch(cv::Exception& e)
    {
        LOGD("nativeCreateObject caught cv::Exception: %s", e.what());
        jclass je = jenv->FindClass("org/opencv/core/CvException");
        if(!je)
            je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, e.what());
    }
    catch (...)
    {
        LOGD("nativeCreateObject caught unknown exception");
        jclass je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, "Unknown exception in JNI code of DetectionBasedTracker.nativeCreateObject()");
        return 0;
    }

    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeCreateObject exit");
    return result;
}

JNIEXPORT void JNICALL Java_org_opencv_samples_facedetect_NativeCodeInterface_nativeDestroyObject
(JNIEnv * jenv, jclass, jlong thiz)
{
    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeDestroyObject enter");
    try
    {
        if(thiz != 0)
        {
            //((DetectionBasedTracker*)thiz)->stop();
            //delete (DetectionBasedTracker*)thiz;
        }
    }
    catch(cv::Exception& e)
    {
        LOGD("nativeestroyObject caught cv::Exception: %s", e.what());
        jclass je = jenv->FindClass("org/opencv/core/CvException");
        if(!je)
            je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, e.what());
    }
    catch (...)
    {
        LOGD("nativeDestroyObject caught unknown exception");
        jclass je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, "Unknown exception in JNI code of DetectionBasedTracker.nativeDestroyObject()");
    }
    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeDestroyObject exit");
}

JNIEXPORT void JNICALL Java_org_opencv_samples_facedetect_NativeCodeInterface_nativeStart
(JNIEnv * jenv, jclass, jlong thiz)
{
    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeStart enter");
    try
    {
        //((DetectionBasedTracker*)thiz)->run();
    }
    catch(cv::Exception& e)
    {
        LOGD("nativeStart caught cv::Exception: %s", e.what());
        jclass je = jenv->FindClass("org/opencv/core/CvException");
        if(!je)
            je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, e.what());
    }
    catch (...)
    {
        LOGD("nativeStart caught unknown exception");
        jclass je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, "Unknown exception in JNI code of DetectionBasedTracker.nativeStart()");
    }
    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeStart exit");
}

JNIEXPORT void JNICALL Java_org_opencv_samples_facedetect_NativeCodeInterface_nativeStop
(JNIEnv * jenv, jclass, jlong thiz)
{
    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeStop enter");
    try
    {
        //((DetectionBasedTracker*)thiz)->stop();
    }
    catch(cv::Exception& e)
    {
        LOGD("nativeStop caught cv::Exception: %s", e.what());
        jclass je = jenv->FindClass("org/opencv/core/CvException");
        if(!je)
            je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, e.what());
    }
    catch (...)
    {
        LOGD("nativeStop caught unknown exception");
        jclass je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, "Unknown exception in JNI code of DetectionBasedTracker.nativeStop()");
    }
    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeStop exit");
}

JNIEXPORT void JNICALL Java_org_opencv_samples_facedetect_NativeCodeInterface_nativeSetFaceSize
(JNIEnv * jenv, jclass, jlong thiz, jint faceSize)
{
    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeSetFaceSize enter");
    try
    {
        if (faceSize > 0)
        {
            DetectionBasedTracker::Parameters DetectorParams = \
            ((DetectionBasedTracker*)thiz)->getParameters();
            DetectorParams.minObjectSize = faceSize;
            ((DetectionBasedTracker*)thiz)->setParameters(DetectorParams);
        }
    }
    catch(cv::Exception& e)
    {
        LOGD("nativeStop caught cv::Exception: %s", e.what());
        jclass je = jenv->FindClass("org/opencv/core/CvException");
        if(!je)
            je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, e.what());
    }
    catch (...)
    {
        LOGD("nativeSetFaceSize caught unknown exception");
        jclass je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, "Unknown exception in JNI code of DetectionBasedTracker.nativeSetFaceSize()");
    }
    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeSetFaceSize exit");
}


JNIEXPORT void JNICALL Java_org_opencv_samples_facedetect_NativeCodeInterface_nativeLoop
(JNIEnv * jenv, jclass, jlong macPtr, jlong imageGray, jlong faces)
{
    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeDetect enter");
    try
    {
        LOGD("passed made it to nativeloop");
        vector<Rect> RectFaces;
        //LOOP CODE
        modelandcascade * mac = (modelandcascade *)macPtr;
        Mat gray = *((Mat *)imageGray);
        Mat resized;
        mac->thecc.detectMultiScale(gray, RectFaces);
        LOGD("passed detectmultiscale");

        vector_Rect_to_Mat(RectFaces, *((Mat*)faces));// what's going on here?

        //Now loop over all of the detected faces in the frame to identify each one.
        LOGD("passed rectfacessize %d",RectFaces.size());
        LOGD("passed themodel address %d", &(mac->themodel));
        //rectfacessize is 1 when pointed at tph's face
        for(int i = 0; i < RectFaces.size(); i++) {
            Size_<int> s = Size(mac->w, mac->h);
            LOGD("passed wh in forloop");
            Mat faceCrop = gray(RectFaces[i]);
            LOGD("passed facecrop in forloop");
            cv::resize(faceCrop,resized, s, 1.0, 1.0, INTER_CUBIC);
            LOGD("passed resize in forloop");
            //got here
            LOGD("passed themodel address in for loop %d", &(mac->themodel));
            int currentp = mac->themodel->predict(resized);
            LOGD("passed currentp in forloop");

            //rectangle(original, RectFaces[i], CV_RGB(0, 255,0), 1);
            //box_text = format("Prediction = %d", currentp);
            Rect r = RectFaces[i];
            LOGD("passed rectr in forloop");
            Point p = r.tl();
            int pos_x = std::max(p.x - 10, 0);
            int pos_y = std::max(p.y - 10, 0);
            LOGD("passed Prediction %d: (%d, %d)", currentp, pos_x, pos_y);

            //putText(original, box_text, Point(pos_x, pos_y), FONT_HERSHEY_PLAIN, 1.0, CV_RGB(0,255,0), 2.0);
        }
        LOGD("passed end of for loop in an iteration");

        //END LOOP CODE


                //((DetectionBasedTracker*)thiz)->process(*((Mat*)imageGray));
                //((DetectionBasedTracker*)thiz)->getObjects(RectFaces);
                //vector_Rect_to_Mat(RectFaces, *((Mat*)faces));


    }
    catch(cv::Exception& e)
    {
        LOGD("nativeCreateObject caught cv::Exception: %s", e.what());
        jclass je = jenv->FindClass("org/opencv/core/CvException");
        if(!je)
            je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, e.what());
    }
    catch (...)
    {
        LOGD("nativeDetect caught unknown exception");
        jclass je = jenv->FindClass("java/lang/Exception");
        jenv->ThrowNew(je, "Unknown exception in JNI code DetectionBasedTracker.nativeDetect()");
    }
    LOGD("Java_org_opencv_samples_facedetect_DetectionBasedTracker_nativeDetect exit");
}
