# CbModel Library #
CbModel is  a library for motion detection based on the paper: <a href='http://umiacs.umd.edu/~knkim/paper/bgs-ICIP2004.pdf'>"<br>
Background Modeling and Subtraction by Codebook Construction"</a>, by L. Davis et. al. (International Conference on Image Processing, ICIP 2004).

## What I need to use CbModel library? ##
CbModel is a library for the <a href='http://processing.org/'>Processing</a> programming environment,
implemented by following <a href='http://dev.processing.org/libraries/'>these</a> guidelines. The library can be use without limitation from any Java program as well.

### Supported Plattform ###
CbModel is operating system independent,tested on <a href='http://www.ubuntu.com/'>Ubuntu </a> platform with Processing 1.0.3

## Documentation ##
_Links_  <a href='http://code.google.com/p/cbmodel/w/list'>Wiki</a>_'s pages_
<ul>
<blockquote><li><b>Installation</b> page(<a href='http://code.google.com/p/cbmodel/wiki/Installation'>view</a>)</li>
<li><b>Download</b> javadocs package(<a href='http://cbmodel.googlecode.com/files/javadocs.zip'>here</a>)</li>
</ul>
<h2>Examples</h2>
Simple example program that analyzes a video (using video library <a href='http://users.design.ucla.edu/~acolubri/processing/gsvideo/home/advanced.html'>GSMovie</a>) and finds the foreground pixels. It uses 50 frames to build the background model and use  the remaining frame for shows the image "difference" (pixel contains white / blacks that indicate the pixel foreground to background, respectively):<br>
<pre><code>import codeanticode.gsvideo.*;
import it.ppm.codebookmodel.*;

GSMovie myMovie;
CbModel Model;
int 	frame=0;
PFont Font;
	
void setup() {
  size(385,630, P3D);	
  background(200);
  Font = loadFont("/home/federico/bin/processing-1.0.3/examples/3D/Typography/Typing/data/Univers45.vlw");
  textFont(Font, 15); 
  myMovie=new GSMovie(this, "/home/federico/Scrivania/ppm/video/walk1.mpg");
  Model=new CbModel(this,384,288);
  print(Model.getVersion());
  fill(0); 
  text("frame:", 0, 310);		
  myMovie.loop();
}

void draw(){
  fill(200);
  rect(50,295,40,15);
  fill(0);
  text(frame, 50, 310);
  if(frame&lt;50){
    if (myMovie.available()) {
      frame=frame+1;   
      myMovie.read();
      image(myMovie, 0,0);
      try{
        Model.updateModel(myMovie);
      }
      catch(LearningStateException Err){
	println("Impossible to pass the state 'test' to the state of 'learning'...");
      }
      catch(WrongSizeException Err){
	println("Dimension of input's image not equal to the size set in the model...");
      }
    }
  }	 
  else{  
    Model.setTestState();
    if(Model.isTestState()){
      if(myMovie.available()){
        frame=frame+1;   
        myMovie.read();
        image(myMovie, 0,0);
        try{
          image(Model.getDifferenceImage(myMovie),0,320);
        }
        catch(WrongSizeException Err){
          println("Dimension");
        }
        catch(LearningStateException Err){
          println("Learn");
        }
      }
    }
  }
}
</code></pre></blockquote>

## Applications ##
Forward there are 3 programs to test the library (**to set the parameters**) in different scenarios:

![http://cbmodel.googlecode.com/files/screen.png](http://cbmodel.googlecode.com/files/screen.png)

| **Filename** | **Use** | **Download** |
|:-------------|:--------|:-------------|
| App\_Codebook | for local video |   (<a href='http://cbmodel.googlecode.com/files/app_codebook 0_1.zip'>here</a>) |
| Webcam\_Codebook | for the stream webcam |   (<a href='http://cbmodel.googlecode.com/files/webcam_codebook 0_1.zip'>here</a>) |
| Streaming\_Codebook | for the internet video stream|   (<a href='http://cbmodel.googlecode.com/files/streaming_codebook 0_1.zip'>here</a>) |

## Release ##
CbModel 0.1 is now available. <br>You can obtain this release (<a href='http://cbmodel.googlecode.com/files/CbModel%200_1.zip'>Here</a>)<br>
and follow  <a href='http://code.google.com/p/cbmodel/wiki/Installation'>these instructions</a> to build it.<br>
<br>
<h2>License</h2>
CbModel is released under the <a href='http://www.gnu.org/licenses/licenses.html'>LGPLv3 license</a>.<br>
<br>
<img src='http://upload.wikimedia.org/wikipedia/commons/8/86/LogoLGPLv3.png' />

<h2>Credit</h2>
CbModel has been developed by Federico Bartoli under <br>the supervision of Dr. <a href='http://www.micc.unifi.it/nunziati/'>Walter Nunziati</a>
<br>and professor <a href='http://www.dsi.unifi.it/~delbimbo/'>Alberto Del Bimbo</a>
The software has been developed within the context of the <a href='http://www.micc.unifi.it/projects/orussi/'>ORUSSI</a> project.<br>
<h2>Contacts</h2>
e-mail: <b>fd.bartoli@gmail.com</b>
<br>
e-mail: <b>walter.nunziati@magentalab.it</b>