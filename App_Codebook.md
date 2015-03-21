# Overview #
This sketch uses the library CbModel for **local video**, it allows you to view the video test and the results obtained from CbModel on the video test.<br>This application also allows you to set the parameters for the library at <b>run-time</b>

<h2>What I need to run App_Codebook sketch?</h2>
App_Codebook  is a sketch  for <a href='http://processing.org/'>Processing</a>,use the <a href='http://users.design.ucla.edu/~acolubri/processing/gsvideo/home/advanced.html'>GSMovie</a> library to extract frames from video<br>
<br>
<h2>How to use</h2>
Launched Sketch, is a fairly intuitive form, the lower are the <b>inputBox</b> to set the parameters:<br>
(if not included are set by default)<br>
<ul><li>alpha - brightness'parameter ,between 0.4-0.7<br>
</li><li>beta - brightness'parameter,tipically between 1.1-1.5<br>
</li><li>percent_tm - temporal threshold's parameter,tipically is 0.5<br>
</li><li>epsilon_1 - max tollerance of brightenns's deviation and the color of a pixel(in    order too recognise a pixel from another) phase's "Learning"<br>
</li><li>frames - number of frames to create the model<br>
</li><li>epsilon_2 - max tollerance of brightenns's deviation and the color of a pixel(in order too recognise a pixel from another) phase's "Testing"(you can <b>change at runtime</b>)<br>
(mandatory parameter)<br>
</li><li>video - name of the local video  (the video <b>must be in the subfolder "video"</b> in the sketch)</li></ul>

After the initialization parameters necessary fields to the library just click on run (green arrow).<br>

Initially being in the process of "learning" is only shown the video and each frame is passed to CbModel to create the model.<br>
Recently the number of frames to create the model (parameter frames), the library passes in the "Testing" and the sketch shows both the video (left) and <br>difference images created by CbModel (on right)<br>
<br>
<h2>Installation</h2>
<h3>STEP ONE: Unpack CbModel</h3>
Extract the compressed file in a part of the system and copy it in the folder libraries of your Processing sketchbook<br>
<br>
<h3>Step TWO: Using the library</h3>
After starting <a href='http://processing.org/'>Processing</a>, go to menu File-> Sketchbook->App_Codebookl