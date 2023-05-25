# ORB-SLAM2-fix-tips


(1)CMakeLists:
find_package(OpenCV REQUIRED)

include/ORBextractor.h
#include <opencv/cv.h>   --->   #include <opencv2/opencv.hpp>


include/PnPsolver.h
#include <opencv2/core/core.hpp>
--->
#include <opencv2/core.hpp>
#include <opencv2/core/core_c.h>

Sim3Solver.cc
add   --->   #include <opencv2/core/core_c.h>

FrameDrawer.cc
#include <opencv2/imgproc/types_c.h>

Tracking.cc
#include <opencv2/imgproc/types_c.h>

LoopClosing.cc
    typedef map<KeyFrame*,                  //键
                g2o::Sim3,                  //值
                std::less<KeyFrame*>,       //排序算法
                Eigen::aligned_allocator<std::pair<KeyFrame*const, g2o::Sim3> > // 指定分配器,和内存空间开辟有关. 为了能够使用Eigen库中的SSE和AVX指令集加速,需要将传统STL容器中的数据进行对齐处理
                > KeyFrameAndPose;


(5)Examples/xxx.cc
#define CV_LOAD_IMAGE_UNCHANGED -1











#define CV_TERMCRIT_ITER cv::TermCriteria::MAX_ITER
#define CV_TERMCRIT_EPS cv::TermCriteria::EPS



