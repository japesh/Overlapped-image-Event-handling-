# Overlapped-image-Event-handling-
 
![alt text](https://github.com/japesh/Overlapped-image-Event-handling-/blob/master/Screenshot%20(31).png "Infinite image with diffrent ckicks")

## Problem statement

Have you ever tried to combine two or more images to combined as single image such as infinity shape?

* Then you faced - Browser render each image in rectangle, which make it difficult to handle events on each image.
* Tab accesibility
* Hove effects

## Solution

1. Create div element of same size all with their corresponding styles and events.
2. Position them at single origin using position property.

   ```
   <style>
     .infinity-tab{
   			width:602px;
   			height: 293px;
   			position: absolute;
   			left:0px;
   			top:0px;
   		}
   		.infinit-tab-list{
   			position: relative;
   		}
     .background-orange {
   			background-color: #fcb040;
   		}
   		.background-blue{
   			background-color:#7498d0;

   		}
   </style>

   <div class="infinit-tab-list">
   			<div class='monitor background-orange infinity-tab' onClick="alert('monitor-clip')"/>
   			<div class='operate background-orange infinity-tab' onClick="alert('operate-clip')"/>
   			<div class='release background-orange infinity-tab' onClick="alert('release-clip')"/>
   			<div class='deploy background-orange infinity-tab' onClick="alert('deploy-clip')"/>
   			<div class='plan background-blue infinity-tab' onClick="alert('plan-clip')"/>
   			<div class='build background-blue infinity-tab' onClick="alert('build-clip')"/>
   			<div class='code background-blue infinity-tab' onClick="alert('code-clip')"/>
   			<div class='test background-blue infinity-tab' onClick="alert('test-clip')"/>
   </div>
   ```

3. [Create svg](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial) images for each image that can be used to clip the div element as follows

    ```
    <svg height="0" width="0">
        <defs>
            <clipPath id="build-clip">
                <path stroke="blue" stroke-opacity="0.8" stroke-width="3" d="M67 31 Q -40 135 53 241 L 101 230 L 99 187 Q 60 135 108 92 L 67 86 Z"/>
            </clipPath>
        </defs>
        <defs>
            <clipPath id="code-clip">
                <path d="M75 25 L 74 77 L 118 83 Q 175 60 222 108 L 225 62 L 274 58 Q 167 -30 75 25"/>
            </clipPath>
        </defs>
        <defs>
            <clipPath id="test-clip">
                <path d="M 107 190 L 110 239 L 58 248 Q 163 311 256 243 L 258 199 L 210 188 Q 155 220 107 190"/>
            </clipPath>
        </defs>
        <defs>
            <clipPath id="release-clip">
                <path d="M 215 182 L 266 192 L 261 240 Q 282 222 301 200 L 350 144 L 377 116 L 372 70 L 323 67 L 303 86 L 254 143 Q 231 170 215 182"/>
            </clipPath>
        </defs>
        <defs>
            <clipPath id="deploy-clip">
                <path d="M 329 60 L 377 63 L 382 112 Q 432 63 485 85 L 529 77 L 529 27 Q 447 -23 329 60"/>
            </clipPath>
        </defs>
        <defs>
            <clipPath id="operate-clip">
                <path d="M 536 30 L 536 86 L 494 91 Q 540 140 498 193 L 496 238 L 545 249 Q 640 145 536 30"/>
            </clipPath>
        </defs>
        <defs>
            <clipPath id="monitor-clip">
                <path d="M 491 198 L 488 244 L 538 254 Q 438 302 352 248 L 350 198 L 395 188 Q 448 224 491 198"/>
            </clipPath>
        </defs>
        <defs>
            <clipPath id="plan-clip">
                <path d="M 388 182 Q 365 161 350 143 L 302 200 Q 315 218 346 242 L 342 192 Z"/>
                <path d="M 302 87 Q 291 73 281 64 L 233 70  L 229 116 Q 240 127 253 143 Z"/>
            </clipPath>
        </defs>
    </svg>
    ```

4. Define clip path to each element with their corresponding id.

    ```
    .build{
        clip-path: url(#build-clip);
    }
    .code{
        clip-path: url(#code-clip);
    }
    .test{
        clip-path: url(#test-clip);
    }
    .release {
        clip-path: url(#release-clip);
    }
    .deploy {
        clip-path: url(#deploy-clip);
    }
    .operate {
        clip-path: url(#operate-clip);
    }

    .monitor {
        clip-path: url(#monitor-clip);
    }

    .plan {
        clip-path: url(#plan-clip);
    }

    ```
5. Now define text field in each div element as follows
   ```
   <div class="infinit-tab-list">
        <div class='monitor background-orange infinity-tab' onClick="alert('monitor-clip')">
            <svg viewBox="0 0 602 293">
                <text >
                    <textPath class="infinity-tab__text"  xlink:href="#monitor-text" fill="#fff">
                    MONITOR
                    </textPath>
                </text>
            </svg>
        </div>
        <div class='operate background-orange infinity-tab' onClick="alert('operate-clip')">
            <svg viewBox="0 0 602 293">
                <text >
                    <textPath class="infinity-tab__text"  xlink:href="#operate-text" fill="#fff">
                    OPERATE
                    </textPath>
                </text>
            </svg>
        </div>
        <div class='release background-orange infinity-tab' onClick="alert('release-clip')">
            <svg viewBox="0 0 602 293">
                <text >
                    <textPath class="infinity-tab__text"  xlink:href="#release-text" fill="#fff">
                    RELEASE
                    </textPath>
                </text>
            </svg>
        </div>	
        <div class='deploy background-orange infinity-tab' onClick="alert('deploy-clip')">
            <svg viewBox="0 0 602 293">
                <text >
                    <textPath class="infinity-tab__text"  xlink:href="#deploy-text" fill="#fff">
                    DEPLOY
                    </textPath>
                </text>
            </svg>
        </div>				
        <div class='plan background-blue infinity-tab' onClick="alert('plan-clip')">
            <svg viewBox="0 0 602 293">
                <text >
                    <textPath class="infinity-tab__text"  xlink:href="#plan-text" fill="#fff">
                    PLAN
                    </textPath>
                </text>
            </svg>
        </div>				
        <div class='build background-blue infinity-tab' onClick="alert('build-clip')">
            <svg viewBox="0 0 602 293">
                <text >
                    <textPath class="infinity-tab__text"  xlink:href="#build-text" fill="#fff">
                    BUILD
                    </textPath>
                </text>
            </svg>
        </div>
        <div class='code background-blue infinity-tab' onClick="alert('code-clip')">
            <svg viewBox="0 0 602 293">
                <text >
                    <textPath class="infinity-tab__text"  xlink:href="#code-text" fill="#fff">
                    CODE
                    </textPath>
                </text>
            </svg>
        </div>
        <div class='test background-blue infinity-tab' onClick="alert('test-clip')">
            <svg viewBox="0 0 602 293">
                <text >
                    <textPath class="infinity-tab__text"  xlink:href="#test-text" fill="#fff">
                    TEST
                    </textPath>
                </text>
            </svg>
        </div>
    </div>
   ```
6. To add curve in text field and to define position of the text element, define path for each text path as follows.
   ```
    <svg height="0" width="0">
        <defs>
            <path id="monitor-text" d="M 363 222 Q 405 258 468 252" />
        </defs>
        <defs>
            <path id="operate-text" d="M 533 103 Q 570 142 529 198" />
        </defs>
        <defs>
            <path id="deploy-text" d="M 402 70 Q 451 37 489 63" />
        </defs>
        <defs>
            <path id="release-text" d="M 286 181 L 341 115" />
        </defs>
        <defs>
            <path id="plan-text" d="M 232 80 L 269 117" />
        </defs>
        <defs>
            <path id="code-text" d="M 118 57 Q 138 38 177 57" />
        </defs>
        <defs>
            <path id="build-text" d="M 39 113 Q 22 146 47 190" />
        </defs>
        <defs>
            <path id="test-text" d="M 137 249 Q 162 257  185 251" />
        </defs>
    </svg>
   ```
7. Highlight the each tab on hover, define as follows.
    ```
    .infinity-tab{
        transition: filter 500ms ease;
    }
    .infinity-tab:hover {
        filter:opacity(0.7);
    }
    ```
