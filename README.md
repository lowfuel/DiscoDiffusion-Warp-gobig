# Disco Diffusion v5.2 - Warp - GO BIG

[![Disco Diffusion v5.2 - Warp](https://colab.research.google.com/github/lowfuel/DiscoDiffusion-Warp-gobig/blob/main/Disco_Diffusion_v5_2_Warp_goBIG.ipynb)

# About
This version improves video init. You can now generate optical flow maps from input videos, and use those to:
- warp init frames for consistent style 
- warp processed frames for less noise in final video

# Going Big
Tick the box for go_big in section 3. 
You also need to know:
- n_batches needs to be 1
- animation mode should be none
- your output won't display, but will be saved - look for the file with "final" in the name and a time stamp (the original is also saved)


##Init warping
The feature works like this: we take the 1st frame, diffuse it as usual as an image input with fixed skip steps. Then we warp in with its flow map into the 2nd frame and blend it with the original raw video 2nd frame. This way we get the style from heavily stylized 1st frame (warped accordingly) and content from 2nd frame (to reduce warping artifacts and prevent overexposure)

# Changelog
### 17.05.2022:
- Go Big mode, symmetry, randomizers
### 22.04.2022:
- Add ViT-L/14@336px
### 21.04.2022: 
- Add warp parameteres to saved settings
### 16.04.2022:
- Use width_height size instead of input video size
- Bring back adabins and 2d/3d anim modes
- Install RAFT only when video input animation mode is selected
- Generate optical flow maps only for video input animation mode even with flow_warp unchecked, so you can still save an obtical flow blended video later
- Install AdaBins for 3d mode only (should do the same for midas)
- Add animation mode check to create video tab 
### 15.04.2022: Init


### Settings: 
(Located in animation settings tab)

Video Optical Flow Settings:
- flow_warp - check to warp
- flow_blend: 0 - you get raw input, 1 - you get warped diffused previous frame 
- check_consistency: check forward-backward flow consistency (uncheck unless getting too many warping artifacts)

##Output warping
This feature is plain simple - we just take any frame, warp in to the next frame, blend with real next frame, get smooth noise-free result.

*note: this notebook completely disables adabins depth estimator and 2d/3d animation due to import name conflicts I'm too lazy to resolve at the moment 😸

### Settings: 
(located in create video tab)
blend_mode: 
- none: just mash frames together in a video
- optical flow: take frame, warp, blend with the next frame
- check_consistency: use consistency maps (may prevent warping artfacts)
- blend: 0 - you get raw 2nd frame, 1 - you get warped 1st frame

## TODO: add automatic flow map management (i.e. create only when needed)

This is a variation of the awesome [DiscoDiffusion colab](https://colab.research.google.com/github/alembics/disco-diffusion/blob/main/Disco_Diffusion.ipynb#scrollTo=Changelog)

If you like what I'm doing you can
- follow me on [twitter](https://twitter.com/devdef)
- check my collections at [opensea](https://opensea.io/collection/ai-scrapers)
- tip me on [patreon](https://www.patreon.com/sxela) 

Thank you for being awesome!
