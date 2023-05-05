Download Link: https://assignmentchef.com/product/solved-cse_ece-478-assignment-2-implementation-of-linear-spatial-filters
<br>
<ol>

 <li> The implementation of linear spatial filters requires moving a mask centered at each pixel of the image, computing sum of products of mask coefficients and corresponding pixels.

  <ol>

   <li>Implement an algorithm for low-pass filtering a grayscale image by moving a <em>k</em>×<em>k </em>averaging filter of the form ones((k,k))/(k<sup>2</sup>).</li>

   <li>As the filter is moved from one spatial location to the next one, the filter window shares many common pixels in adjacent neighborhoods. Exploit this observation and implement a more efficient version of averaging filter.</li>

   <li>To appreciate the benefits of doing so, generate a plot of <em>k </em>vs run-time for various sized images. The plot diagram should contain a line plot for each image size you pick. Use different marker types to distinguish the default implementation and improved implementation. Just to give you a rough idea, look at <a href="https://imgur.com/a/0HtYlTE">https: </a><a href="https://imgur.com/a/0HtYlTE">//imgur.com/a/0HtYlTE</a><a href="https://imgur.com/a/0HtYlTE">.</a></li>

   <li>Utilize the observation similar to above to implement an efficient version of a <em>k</em>×<em>k </em>median filter. Generate a plot figure similar to previous question.</li>

   <li>Using the denoising concepts discussed in the class, try to remove noise from</li>

  </ol></li>

</ol>

<strong>Noisy.jpg</strong>

<ol start="2">

 <li> Edge Detection

  <ol>

   <li>Read about Canny Edge detector. Apply the Canny edge detector (use inbuilt <em>Canny </em>function for this task) to bell.jpg.</li>

   <li>Tweak the values of the arguments (<em>minVal </em>and <em>maxVal</em>), and report the values that give the best results for each image. (Hint: Try to detect as many edges in the bell as possible, while avoiding edges in the background.).</li>

   <li>Consider <strong>Roberts, Prewitt, Sobel and Laplacian </strong>filters discussed in the class. Implement and apply these filters on png and make observations upon comparing their outputs. Compare these with the output of Canny edge detector on the same image.</li>

  </ol></li>

</ol>

Figure 1: Prewitt, Roberts and Sobel filters

Figure 2: Two forms of the laplacian filter

<ol start="4">

 <li>What will the 5×5 variants of <strong>Sobel and Prewitt </strong>filters look like? Apply these larger filters on png and make observations upon comparing their outputs with the corresponding smaller filters.</li>

 <li>Add noise to the input image above using Gaussian sampling. Study the effect of applying the above filters(from 2<em><sup>nd </sup></em>part) on noise-affected inputs.</li>

</ol>

<ol start="3">

 <li> Bilateral Filtering

  <ol>

   <li>Implement Bilateral Filtering and apply it on <strong>jpg</strong></li>

   <li>In low light imaging, images tend to be noisy and lose sharp edges. However, with flash, there is an unpleasant direct-lighting effect. Here, a <strong>cross bilateral filter </strong>can be used with the range and spatial filters acting on two different images.</li>

   <li>By combining a flash photograph <strong>cake-flash.jpg </strong>and a no-flash photograph <strong>jpg</strong>, render a new photograph <strong>cake-out.jpg </strong>that has both the warm lighting of the no-flash picture and the crisp details of the flash image.</li>

  </ol></li>

</ol>

Figure 3: flash, no-flash and output images

<strong>Note: </strong>This question has to be done on RGB images. For applying filters on RGB images you can do the same filtering operation used on grayscale image for each channel (i.e., R,G,B) separately, one by one.

<strong>Reference link </strong>– <a href="https://people.csail.mit.edu/sparis/bf_course/course_notes.pdf">https://people.csail.mit.edu/sparis/bf_course/course_notes</a>. <a href="https://people.csail.mit.edu/sparis/bf_course/course_notes.pdf">pdf</a>

<ol start="4">

 <li> In order to achieve a basic cartoon effect, all you need is essentially – a bilateral filter and some edge detection. The bilateral filter will reduce the color palette, necessary for the cartoon look, and edge detection will allow production of bold silhouettes. To get cartoonized effects following steps are needed –

  <ol>

   <li>Apply the bilateral filtering to the color image. Keep this filtered image aside for the last step.</li>

   <li>Now, take a copy of original color image, <strong>convert it to gray scale</strong>.</li>

   <li><strong>Apply blurring </strong>on this gray scale image to reduce noise. (Try different variants of blurring and see the performance)</li>

   <li>Now, <strong>create an edge mask </strong>from this blurred, gray scale image. An edge mask can be obtained using adaptive thresholding.</li>

   <li>Combine the bilateral filtered image from step 1 with edge mask(by taking bitwise AND of both at each pixel location).</li>

  </ol></li>

</ol>

Figure 4: Sample cartoon image

Now try to do these for images of your choice. Feel free to experiment with different filters and even methods to generate even better cartoons.

<strong>Note: </strong>This question has to be done on RGB images only. But you can work on each channel separately, and then combine them for final image.

<ol start="5">

 <li> Fourier Transform

  <ol>

   <li>Implement 2D DFT.</li>

   <li>Implement 1D Fast Fourier Transform (Recursive Formulation). Use it to implement 2D FFT and display the result on suitable images of your choice. Compare the run times of your version of DFT and FFT on different sized inputs and plot them.</li>

   <li>Now, implement 2D Inverse FFT in a similar fashion.</li>

   <li>Calculate the Fourier transform of the Fourier transform of any image. You would observe that the image you get is similar to the original image. How is it different from the original image? How can you fix this in the frequency domain so that we would get the original image back instead?</li>

  </ol></li>

 <li>Pick two images f,h of same dimension (256 × 256). Compute their respective Fourier transforms F, H.

  <ol>

   <li>Compute IFT(F.H) and f * h. Check whether IFT(F.H) corresponds to the center portion of f * h. Compute the average of squared difference between pixel values in IFT(F.H) and the central 256 × 256 portion of f * h (F.H denotes point-wise multiplication of F and H and f * h denotes convolution with padding).</li>

   <li>What changes do you observe when you zero pad the original images to dimension (511 × 511) and now calculate IFT(F.H) and report the new error. Choose any 64×64 image. Now, add 64 columns and rows of zeros to the right and bottom side</li>

  </ol></li>

</ol>

of the original image. Repeat this process two more times each time doubling the image size and padding the pixels on the right and bottom by zeroes. You will therefore have 4 images first one 64 × 64 with no zero padding and then 128 × 128, 256 × 256 and 512 × 512 after padding. Find the Fourier transform of all these images. Display the results and explain and justify the relationship between the four outputs you get.

<ol start="7">

 <li> Denoise the given image <strong>noisy-lena.png </strong>and explain your process.</li>

</ol>