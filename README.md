# Issues-I-had-when-Installing-Matconvent+ Matlab-Python - GPU- VOT-TRAX 

Downloads:

From Add-On in Matlab setup Parallel Computing Toolbox

MatConvent:
https://www.mathworks.com/matlabcentral/fileexchange/47811-vlfeat-matconvnet

VS2015
https://my.visualstudio.com/Downloads?q=Visual%20Studio%202015%20with%20Update%203

CUDA & CUDNN
1. https://docs.nvidia.com/deeplearning/sdk/cudnn-install/index.html#installcuda-windows
2. https://developer.nvidia.com/rdp/cudnn-download

Choose the suitable version for your Windows, GPU.

+ Visual Studio 2017 doesnt work with Matlab 2017b in case of installing Matconvent
+ Instead use VS2015

+ Dont forget to add CUDNN to CUDA9.0
+ Becarful after you add CUDNN python doesnt work.

+ To explore which compiler you want to use (VS2017, VS2015) in case you have both just type in matab  mex -setup 
  it allows you to choose one.
  
  VOT and TRAX installation
  =========================
  
1. I downloaded TRAX from here https://github.com/alessiodore/trax
2. Replace every xrange by range if any
3. Vot toolkit/ tracker/ System_wrapper.m I added this line before line#176 

#Instead of# :

	    [status, output] = system(tracker.commandcomand, '');
#ADD#

            command= string(sprintf('python %s', tracker.command));
	    [status, output] = system(command, '');
        
 4. In Trax.py add import fuctools
 5. At line 392   
 #instead of#
 
            assert(reduce(lambda x,y: x and y, [isinstance(p,tuple) for p in points], False))
 #ADD#
 
            assert(functools.reduce(lambda x,y: x and y, [isinstance(p,tuple) for p in points], False))
         
 6. If map function doesnt have length add list before map.
 
 7. The same for all trax files (e.g. Images, Region,...)
 
 8. For CCOT Tracker use this toolkit version https://github.com/votchallenge/vot-toolkit/tree/64da0655cf973ef4a32923c72d5c423f908325a5
 9. How to install CCOT tracker https://github.com/martin-danelljan/Continuous-ConvOp
 10. ECO trackerhttps://github.com/martin-danelljan/ECO
   When you run it and gives you error message Make sure you integrate CUDNN (Just add folders to CUDA) and also be sure that IMAGENET    it had  been downloaded 
   
11. When you download any tracker from VOT-Challenge http://www.votchallenge.net/challenges.html Don't forget to check the MATCONVENT version (depends on your OS and GPU) they use otherwise delete their MATCONVENT  and put yours 


Other issues 
____________

After installing CUDNN when you run Matlab (Run_expierment.m in Vot-workspace) it will give you erro

to fix it you have to remove CUDnn files form (bin, lib, include folders).

Don't run Matlab in VOT while python Anaconda-Spyder is running).

Number of folders (seuqences in VOT/results folder for each tracker) should be the same for other trackers


 
        
        
  
   
