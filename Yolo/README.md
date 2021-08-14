we are all hearing about self-driving cars , Tesla , Comma Ai , elon musk ... but have we ever asked ourselves how can you that , how can these systems detect object , avoid objects and prevent accidents by a high accuracy of detecting dangers , in this articles ( REadMe) i will explain how those models ,systems achieved the state-of-art in detecting objects 
let's dive into the YOLO object localization model , you only look once , it is extremly fast since it predicts multiple Bounding boxes simultaneously By by processing the full image 
how Yolo Works ? 
Yolo is a Model that detects objects in a seperate way , one image can be cut to 19x19 ( the number depends on how you cut you training data) grid cells so the model can predict cells , ![image](https://user-images.githubusercontent.com/47725118/129443462-f90ea33c-2e15-4b0b-a502-3ccd89b8184f.png)
for each grid cell , we have the following labels for training 
![image](https://user-images.githubusercontent.com/47725118/129443479-652ae1ca-46d7-4d8a-8f8d-6563d697eb78.png)
notice that the cell grid with the center point , it's Pc = 1 , Pc is the confidence score , it reflects how confident the model is  , that the box contains an object and also how accurate it thinks the box  is that it predicts , the confidence is defined as  Pr(Object) ∗ IOU(truth,pred) , Pr(object) is the probability that a grid cell contains an object 
