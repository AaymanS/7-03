-----------------------------------------------------------------------------------------
-- Created by: Aayman Shameem
-- Created on: Apr 23, 2018
-- This code will give gravity to the character
-----------------------------------------------------------------------------------------

-- Gravity

local physics = require( "physics" )

physics.start()
physics.setGravity( 0, 25 ) -- ( x, y )
physics.setDrawMode( "hybrid" )   -- Shows collision engine outlines only

local theGround = display.newImage( "./assets/sprites/land.png" )
theGround.x = display.contentCenterX
theGround.y = display.contentHeight
theGround.id = "the ground"
physics.addBody( theGround, "static", { 
    friction = 0.5, 
    bounce = 0.3 
    } )

local theGround2 = display.newImage( "./assets/sprites/land.png" )
theGround2.x = display.contentCenterX + 800
theGround2.y = display.contentCenterY + 100
theGround2.id = "the ground"
physics.addBody( theGround2, "static", { 
    friction = 0.5, 
    bounce = 0.3 
    } )

local monsterCat = display.newImage( "./assets/sprites/Monstercat.png" )
monsterCat.x = display.contentCenterX + 900
monsterCat.y = display.contentCenterY - 500
monsterCat.id = "the character"
monsterCat.isFixedRotation = true
physics.addBody( monsterCat, "dynamic", { 
    density = 3.0, 
    friction = 0.5, 
    bounce = 0.3 
    } )

local dPad = display.newImage( "./assets/sprites/d-pad.png" )
dPad.x = 150
dPad.y = display.contentHeight - 150
dPad.id = "d-pad"

local upArrow = display.newImage( "./assets/sprites/upArrow.png" )
upArrow.x = 150
upArrow.y = display.contentHeight - 260
upArrow.id = "up arrow"

local downArrow = display.newImage( "./assets/sprites/downArrow.png" )
downArrow.x = 150
downArrow.y = display.contentHeight - 40
downArrow.id = "up arrow"

local leftArrow = display.newImage( "./assets/sprites/leftArrow.png" )
leftArrow.x = 40
leftArrow.y = display.contentHeight - 150
leftArrow.id = "up arrow"

local rightArrow = display.newImage( "./assets/sprites/rightArrow.png" )
rightArrow.x = 260
rightArrow.y = display.contentHeight - 150
rightArrow.id = "up arrow"
 
function upArrow:touch( event )
    if ( event.phase == "ended" ) then
        -- move the character up
        transition.moveBy( monsterCat, { 
        	x = 0, -- move 0 in the x direction 
        	y = -50, -- move up 50 pixels
        	time = 100 -- move in a 1/10 of a second
        	} )
    end

    return true
end

function downArrow:touch( event )
    if ( event.phase == "ended" ) then
        -- move the character up
        transition.moveBy( monsterCat, { 
        	x = 0, -- move 0 in the x direction 
        	y = 50, -- move up 50 pixels
        	time = 100 -- move in a 1/10 of a second
        	} )
    end

    return true
end

function leftArrow:touch( event )
    if ( event.phase == "ended" ) then
        -- move the character up
        transition.moveBy( monsterCat, { 
        	x = -50, -- move 0 in the x direction 
        	y = 0, -- move up 50 pixels
        	time = 100 -- move in a 1/10 of a second
        	} )
    end

    return true
end

function rightArrow:touch( event )
    if ( event.phase == "ended" ) then
        -- move the character up
        transition.moveBy( monsterCat, { 
        	x = 50, -- move 0 in the x direction 
        	y = 0, -- move up 50 pixels
        	time = 100 -- move in a 1/10 of a second
        	} )
    end

    return true
end

upArrow:addEventListener( "touch", upArrow )
downArrow:addEventListener( "touch", downArrow )
leftArrow:addEventListener( "touch", leftArrow )
rightArrow:addEventListener( "touch", rightArrow )
