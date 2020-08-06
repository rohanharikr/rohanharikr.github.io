---
layout: post
title: Top down character movement in Lua using love2d
description: ''
summary: ''
comments: true
tags:
- love2d

---
<iframe src="[https://player.vimeo.com/video/445251655](https://player.vimeo.com/video/445251655 "https://player.vimeo.com/video/445251655")" width="640" height="480" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

So, first we will have to load up the sprites for this. I have used the sprites from the Bloodborne pixel art game "Yarntown" which can be found [here](https://github.com/MaxMraz/yarntown).

_spritesheethere_

I defined some variables in the main.lua, will explain these as we go.

    local player
    local sprite
    local spriteWidth = 16
    local spriteHeight = 25
    localcurrentFrame = 0
    local totalFrames = 8
    local frames = 0
    localframeDelay = 0.1
    local playerX = 150
    local playerY = 150
    local speed = 2.8
    local hunter

The sprite variable just stores our spritesheet and player references a single frame of the spritesheet.

love2d has three main functions: load(), update() and draw() just like any other framework out there.

Let's load up our assets.

    function love.load()
    	love.graphics.setDefaultFilter("nearest")
    	sprite = love.graphics.newImage("hunter_hero.png")
    	player = love.graphics.newQuad(0, 0, spriteWidth, spriteHeight, sprite:getDimensions())
    end

Line 2 does nothing but tells love2d to render graphics as it is without applying any anti-aliasing, so we get the pixel perfect look we are going for.

Line 3 references the spritesheet of the name "hunter_hero.png" in the same directory and Line 4 tells love2d to look for one frame in the sheet.

Let's take a closer look at the parameters:

0, 0: x and y coordinate which in our case is the top-left where our sprite starts.

spriteWidth, spriteHeight: Since I know the size of one single frame beforehand, I am passing this to the function. spriteWidth and spriteHeight has already declared values.

Ideally every sprite in the spritesheet should be of same width and height.

sprite:getDimensions(): Just returns the width and height of the spritesheet. 

To check if it works, just draw our player variable in the draw function. You should be able to see the first frame.

Remember to keep the code in the main file to a minimum because this is where the entire game code comes together. Ideally, the code should be broken up into input/controls, charaters, etc. For the sake of demostration, I am putting everything in the main file.

    function love.update(dt)
    	frames = frames + dt
        if love.keyboard.isDown("left") then
        	playerX = playerX - speed
            if frames >= frameDelay then
            	frames = 0
    	        if currentFrame >= totalFrames then
            		currentFrame = 0
        	    end
    	        player = love.graphics.newQuad((spriteWidth * currentFrame), 63, spriteWidth, spriteHeight, sprite:getDimensions())
        	    currentFrame = currentFrame + 1
    		end
    	end
    end

All this code is doing is on left keyboard arrow click, move the player -x and play the left walk animation. dt is nothing but delta time meaning the time bet