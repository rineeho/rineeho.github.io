
#### 미완성 포스팅으로 아직 틀린 부분이 많습니다.

![Figure](_images/neural_artist_1.jpg)

본 논문의 개념을 한 장의 이미지로 설명하고 있습니다. Input image는 두 장이 필요합니다.
1.스타일을 빼올 이미지와 2.컨텐츠를 빼올 이미지 여기서는 고흐의 그림 스타일을 풍경 이미지에 녹여내고자 하는 예시를 들었습니다.

먼저 가운데에 있는 CNN(Convolutional Neural Network)은 이미 기존에 ImageNet 데이터를 이용하여 학습이 된 image classification 모델입니다(VGG-Network).

#### Content Reconstructions
(a) conv1_1, (b) conv2_2, (c) conv3_1, (d) conv4_1, (e) conv5_1 을 통과한 input image를 reconstruction 한 것입니다. (a-c)의 경우 거의 원본과 유사할 정도로 reconstruction이 잘 된 것을 볼 수 있습니다. higher layer의 경우 detail은 좀 loss가 있지만, high-level content 즉, 집의 구조나 전체적인 틀은 잘 보존이 되어 있습니다.

#### Style Reconsturctions
input image의 style을 잘 잡아낸 새로운 feature space를 만들어 냈습니다. style representation의 경우 CNN의 여러 다른 layer에 있는 여러 feature들 같의 correlation을 합니다.
CNN의 여러 layer들의 조합으로 style representation을 계산하여 표현했는데,
(a) conv1_1, (b) conv1_1과 conv2_1의 조합, (c) conv1_1, conv2_1, conv3_1, (d) conv1_1, conv2_1, conv3_1, conv4_1, (e)는 (d) + conv5_1 (쓰기 귀찮..)
이렇게 하면, 장면의 전체적인 배치 정보를 버리면서 이미지의 스타일만을 남겨놓는 이미지를 만들게 됩니다.
