# final_project
## Summary
+ StandardScaler 이용하여 데이터 전처리  
+ logistic regression 이용하여 olivetti dataset 학습  
+ GirdSearchCV 이용하여 hyperparameter 최적화  

## Olivetti dataset
`This dataset contains a set of face images`_ taken between April 1992 and 
April 1994 at AT&T Laboratories Cambridge. The
:func:`sklearn.datasets.fetch_olivetti_faces` function is the data
fetching / caching function that downloads the data
archive from AT&T.

.. _This dataset contains a set of face images: http://www.cl.cam.ac.uk/research/dtg/attarchive/facedatabase.html

As described on the original website:

    There are ten different images of each of 40 distinct subjects. For some
    subjects, the images were taken at different times, varying the lighting,
    facial expressions (open / closed eyes, smiling / not smiling) and facial
    details (glasses / no glasses). All the images were taken against a dark
    homogeneous background with the subjects in an upright, frontal position 
    (with tolerance for some side movement).

**Data Set Characteristics:**

    =================   =====================
    Classes                                40
    Samples total                         400
    Dimensionality                       4096
    Features            real, between 0 and 1
    =================   =====================

The image is quantized to 256 grey levels and stored as unsigned 8-bit 
integers; the loader will convert these to floating point values on the 
interval [0, 1], which are easier to work with for many algorithms.

The "target" for this database is an integer from 0 to 39 indicating the
identity of the person pictured; however, with only 10 examples per class, this
relatively small dataset is more interesting from an unsupervised or
semi-supervised perspective.

The original dataset consisted of 92 x 112, while the version available here
consists of 64x64 images.

When using these images, please give credit to AT&T Laboratories Cambridge.

## Code explanation

+ Logistic Regression 알고리즘을 통해 데이터셋을 학습함.
  + 로지스틱 회귀는 영국의 통계학자인 D. R. Cox가 1958년에 제안한 확률 모델로서 독립 변수의 선형 결합을 이용하여 사건의 발생 가능성을 예측하는데 사용되는 통계 기법으로, 데이터가 어떤 범주에 속할 확률을 0에서 1 사이의 값으로 예측하고 그 확률에 따라 가능성이 더 높은 범주에 속하는 것으로 분류해주는 지도 학습 알고리즘임.
  
+ 적은 iteration에서 모델이 수렴할 수 있도록 scikit-learn에 내장된 StandardScaler을 이용하여 데이터를 scale함.
  
  
+ Hyperparameter 최적화를 위하여 scikit-learn에 내장된 GirdSearchCV을 사용함.  
  + Hyperparameter 최적화는 tol값과 C값에 대하여 수행함.  
  + param_grid에 들어가는 tol값과 C값은 numpy의 linspace를 이용하여 특정 범위 내에서 일정한 간격을 두고 생성하였으며, 범위를 좁혀가며 최적화를 수행함. 
  + tol은 iteration마다 목표로 하는 손실함수의 감소치를 나타내는 parameter로, 손실 함수의 값이 이 값만큼 감소되지 않으면 iteration을 중단함.  
  + C는 규제의 강도와 관련된 parameter로, 이 값이 클수록 약한 규제가 적용되어 모델이 복잡해져 정확도가 향상되지만, 과도하게 높은 값으로 설정할 경우 과적합을 유발함.   


## License
[MIT license](https://github.com/pwnstj/oss_final/blob/main/LICENSE)
## Contact
arps1214@gmail.com
