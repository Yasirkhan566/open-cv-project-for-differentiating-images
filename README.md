# open-cv-project-for-differentiating-images
Using Open CV differentiate between two images. Finds difference between Two images.

<h2>There are few things that you should know before moving to the code.</h2>
<ol>
  <li>cv2.findContours</li>
  <li>Thresholding</li>
  <li>Upscaling Features</li>
</ol>

<h2>cv2.findContours</h2>
<p>cv2.findContours is an OpenCV function used to detect contours in a binary image. Contours are curves joining all continuous points along a boundary having the same color or intensity. They are useful for shape analysis, object detection, and image segmentation. Here's a detailed explanation of how cv2.findContours works:</p>

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

<ol>
<li><b>contours:</b> A list of detected contours. Each contour is represented as a list of points.</li>
<li><b>hierarchy:</b> Optional output. Contains information about the image topology and the hierarchical relationship of contours.</li>
</ol>
