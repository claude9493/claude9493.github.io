---
layout: post
title: Hough transformation and its broad applications
excerpt_separator:  <!--more-->
---

# Hough transformation and its broad applications

Hough transformation, an efficient method for recognizing complicated pattern (Hough, P.V.C. 1962), is one of the most essential algorithms in the field of computer vision. It was invented by Hough who was an American engineer working in an atomic energy researching institute in 1962 and advanced and extended by many researchers after it being invented. <!--more-->This method is applied in plenty fields which have to face the puzzle of pattern recognizing, including geography, traffic, biological engineering and physics (Tarsha-Kurdi, F. 2007. Liu. H. 2010. Guan, P. P. 2011. CALICE collaboration. 2017. Ballard. 1981), which fully shows importance of this method. In this present paper, some examples of Hough transformation's application in diverse fields are reviewed to present its principle and function.
- - - -
In the research paper by F.Tarsha-Kurdi (2007), an efficient model for automatically detecting 3D building roof is yielded.(Tarsha-Kurdi, F. 2007) From the LIDAR (Laser Intensity Direction and Ranging) point cloud data, the algorithm looked for point sets which represented statistically the best planes. It first mapped the data from points in OXYZ space to sinusoidal surface in the Oθφρ space which was stored in a 3D matrix. Then it detected the peaks from the matrix by searching voxels having the maximum values and mapped them to planes in OXYZ space. Finally taking a 3D region growing algorithm, the roof would be detected successfully. Except of point cloud data, normal image data can be used as data source in Hough transformation as well.

In the research paper by Hong Liu (2010), a method for automatically elevator passengers counting was introduced. The idea was generated from the Circle Hough Transformation which is an extension of original transformation-which was used to detect circles or ellipses, and the round shape of human head. It first extracted the foreground of the image and de-noised it, in order to reduce the interference of the elevator body and unrelated objects. Then the HCT (Hough Circle transformation) algorithm transformed the data from processed image to a matrix of abr parameters space and sought the local maximal points. After transforming these points back to the original space and mapping the circles on the image, each passenger would be marked by the generated circle. (Liu. H. 2010) What’s interesting, almost same method can be applied in the work of segmenting blood cell image (Guan, P. P. 2011).

Pearl P. Guan presented a method for the segmentation of blood cells (Guan, P. P. 2011), which was based on the Circle Hough Transformation and fuzzy curve tracing. It could extract the smooth cell boundaries accurately regardless of the noise and brightness factors. First, the researchers extracted the edge points using the Sobel operator from the grayscale image of original cell image. Taking the advantage of the similar circle shape of a blood cell, the Hough transformation worked just as Hong Liu did in her research of automatically detecting persons (Liu. H. 2010). It transformed the edge pixels in the cell image to the points in parameter space and counting the valid points. Then it gave an accurate result. In the real experiments, facing slightly overlapping cells, Hough transformation even unexpectedly separated them well.
Returning to the original intention of Hough transformation, it was first invented to automate the tedious task of detecting and plotting the tracks of subatomic particles in bubble chamber photographs. The transformation is still used in the research of high-energy and particle physics. In CALICE (CAlorimeter for LInear Collider Experiment) Collaboration’s research paper, Hough Transformation was used to separate the charged particles’ track segments from the highly dense environment present in showers produced by high-energy hadrons. (CALICE collaboration. 2017) Layers of SDHCAL was segmented into about ten thousand pads which were read out by independent electronic channels providing a semi-digital information. After pre-processing these information, the clusters of its resulting is processed by Hough transformation several times and eliminated tracks are generated with high accuracy. Besides, in the theorem research field, Hough transformation has been enhanced greatly as well.

Actually only about twenty years after Hough patented his transformation method, an enhanced version of Hough transformation which was able to detect arbitrary shapes was proposed by D. H. Ballard in 1980. In his paper, he identified the principle of the generalization process which was mapping from edge space to accumulator space described as a table of edge-orientation reference-point correspondence termed an R-table. He also gave some examples of such algorithm (Ballard. 1981). Thanks to this research, Hough transformation was able to be applied to more complex situations but this method was limited by its high costs of computing power which restricted its applications in other fields at that time.
Till now five applications of Hough transformation are introduced above, which strongly proved the hypothesis of this article. The studies on Hough transformation made it possible to let machines automate recognizing patterns in terms of building roof, person’s head, blood cells or subatomic particles (Tarsha-Kurdi, F. 2007. Liu. H. 2010. Guan, P. P. 2011. CALICE collaboration. 2017. Ballard. 1981). Thanks to Hough transformation, possible solutions to one of the three ‘R’s (Recognition, Reconstruction and Reorganization) about computer vision (Malik, J. 2016) is given. In further research, the Hough transformation will keep popular in academic research and combine with Neural network, artificial intelligence and many other new technologies.
 
## References

- Ballard, D. H. (1981). Generalizing the Hough transform to detect arbitrary shapes. Pattern recognition, 13(2), 111-122.

- CALICE collaboration. (2017). Tracking within Hadronic Showers in the CALICE SDHCAL prototype using a Hough Transform Technique. arXiv preprint arXiv:1702.08082.

- Guan, P. P., & Yan, H. (2011). Blood cell image segmentation based on the Hough transform and fuzzy curve tracing. International Conference on Machine Learning and Cybernetics (Vol.4, pp.1696-1701). IEEE.

- Hough, P.V.C. (1962, December 18). METHOD AND MEANS FOR RECOGNIZING COMPLEX PATTERNS. United States.

- Liu, H., Qian, Y., & Lin, S. (2010). Detecting Persons using Hough Circle Transform in Surveillance Video. Visapp 2010 - Proceedings of the Fifth International Conference on Computer Vision Theory and Applications, Angers, France, May (pp.267-270). DBLP.

- Malik, J., Arbeláez, P., Carreira, J., Fragkiadaki, K., Girshick, R., Gkioxari, G., ... & Tulsiani, S. (2016). The three R’s of computer vision: Recognition, reconstruction and reorganization. Pattern Recognition Letters, 72, 4-14.

- Mukhopadhyay, P., & Chaudhuri, B. B. (2015). A survey of Hough Transform. Pattern Recognition, 48(3), 993-1010.

- Tarsha-Kurdi, F., Landes, T., & Grussenmeyer, P. (2007, September). Hough-transform and extended ransac algorithms for automatic detection of 3d building roof planes from lidar data. In ISPRS Workshop on Laser Scanning 2007 and SilviLaser 2007 (Vol. 36, pp. 407-412).



