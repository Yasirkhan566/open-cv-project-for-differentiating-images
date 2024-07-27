# open-cv-project-for-differentiating-images
Using Open CV differentiate between two images. Finds difference between Two images.

<h2>There are few things that you should know before moving to the code.</h2>
<ol>
  <li>cv2.findContours</li>
  <li>Thresholding</li>
  <li>Upscaling Features</li>
</ol>

<h2>1- cv2.findContours:</h2>
<p>cv2.findContours is an OpenCV function used to detect contours (boundry box dimension and position) in a binary image. Contours are curves joining all continuous points along a boundary having the same color or intensity. They are useful for shape analysis, object detection, and image segmentation. Here's a detailed explanation of how cv2.findContours works:</p>

<h3>How cv2.findContours Works</h3>
<h4>Input Image:</h4>

<p>cv2.findContours requires a binary image as input, where the objects to be detected are in white (pixel value 255) and the background is black (pixel value 0).
Typically, a grayscale image is thresholded using methods like cv2.threshold or cv2.Canny edge detection to produce such a binary image.</p>

<h4>Parameters:</h4>

<p><b>image</b>: The source, binary image. This image should be preprocessed to be binary (only containing black and white pixels).</p>
<p><b>mode:</b> The contour retrieval mode. Common modes include:</p>
<ul>
<li><b>cv2.RETR_EXTERNAL:</b> Retrieves only the extreme outer contours.</li>
<li><b>cv2.RETR_LIST:</b> Retrieves all of the contours without establishing any hierarchical relationships.</li>
<li><b>cv2.RETR_TREE:</b> Retrieves all of the contours and reconstructs a full hierarchy of nested contours.</li>
</ul>
<p></p><b>method:</b> The contour approximation method. Common methods include:</p>
<ul>
<li><b>cv2.CHAIN_APPROX_NONE:</b> Stores all the contour points. This results in storing many points for curves.</li>
<li><b>cv2.CHAIN_APPROX_SIMPLE:</b> Compresses horizontal, vertical, and diagonal segments and leaves only their end points. For example, a rectangle contour is encoded with only four points.</li>
</ul>

<h4>Output:</h4>

<ul>
<li><b>contours:</b> A list of detected contours. Each contour is represented as a list of points.</li>
<li><b>hierarchy:</b> Optional output. Contains information about the image topology and the hierarchical relationship of contours.</li>
</ul>

<h1>Key Point:</h1>
<p>From above function you have noticed that cv2.findContours function only take binary image. So we need to convert our images to binary (Gray Scale)</p>
<p>Gray scale images can be producted using cv2.cvtColors function</p>

<h3>Now we need to prepare the difference image that we can pass as input to findContours Function.<br>The difference image will contain white spots on black background. The white spots will be the difference</h3>
<h5>How can we make difference image?</h5>
<p>We will use gray scale images to make differece image. There is a builtin function in skimage library. Function name structural_similarity. This function will calculate structural similarity index between two images and produces a differnce image. The differnce image is gray scale with features magnitude in range 0 to 1</p>

<h5>There is a problem. That the findContours function takes image having features ranging from 0 to 225 and their data type as unit8 (unsigned int 8 bit). But our differnce image has features range from 0 to 1 and thier datatype is float 64 bit. So first we need to covert the difference image into appropriate format for this we will do <b>feature scaling and unit conversion</b></h5>

<h3>How we do feature scaling?</h3>
<p>we will do feature scaling using <b>thresholding</b>. Follow the link to read the article on thresholding on Open CV website. <a href="https://docs.opencv.org/3.4/d7/d4d/tutorial_py_thresholding.html">Click Me</a></p>

<h1>Summary</h1>
<ol>
  <li>Create Gray Scale images from inptut images</li>
  <li>Find diff image using structural_similarity function</li>
  <li>convert diff to unsigned int 8 bit and Scale features in range 0 to 255</li>
  <li>Use diff to find contours</li>
  <li>loop through each countour in countours to draw bounded boxes on input images</li>
  <li>show images</li>
</ol>


