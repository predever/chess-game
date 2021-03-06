# ... Description of your project and this makefile target ... #
# ...   keep in mind you must fill all required variables  ... #
        
        ###             ~ Web App Builder ~               ###
        #       a Makefile to compile a web project.        #
        #  designed for web project with different devices  #
        #  (mobile, tablet, desktop) but with common code.  #
        ###        by @greweb  -  http://greweb.fr/       ###

# export DEBUG=true

  # BUILD_DIR : PATH to WebAppBuilder/build directory (the directory containing all build tools)
BUILD_DIR = ../WebAppBuilder/build

  # SRC_DIR : the source directory
SRC_DIR = ../src

  # DIST_DIR : the dist directory (ex: assets for android, www for iphone)
  # this should not be "." because the directory will be removed on clean
DIST_DIR = assets

  # RESOURCES : Your assets (images, sounds, fonts... and other static files)
# You can rename dist file by prefix newname= ( ex: index.html=iphone_version.html )
RESOURCES = images Chewy.ttf background.jpg icon.png

  # VIEWS : Views will be interpreted by Mustache.js
  # You can pass arguments with JSON format.
  # Example: index.html:"{key1:value1,key2:value2,...}"  <= no spaces!
VIEWS = index.html=game.html:"{version:'1.0'}"

  ### SCRIPTS : all javascripts
  # - You can pass an URL to retrieve
  # - if you want to minimize the JS, prefix with '!'
  # - to mix scripts, concat them with a comma ','
  # - to set the destination name, you can prefix scripts with 'myname.js=' else the first script name is used ( exemple: all.js=util.js,ui.js,main.js ).
SCRIPTS = game.min.js=!game.js lib.min.js=underscore-min.js,zepto.min.js
#jquery.min.js=http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js

  ### STYLES : all styles : CSS or SASS
  # - For .sass files, we compile them to css
  # - Like before, you can mix styles with ',' and you can name your target by prefixing 'name='
STYLES = game.css=mobile.sass

########################################################################


all: welcome clean assets_views assets_scripts assets_styles assets_files

welcome:
	@@${BUILD_DIR}/welcome.sh

assets_base: 
	@@mkdir -p ${DIST_DIR}

assets_views: assets_base
	@@${BUILD_DIR}/compile_views.sh ${SRC_DIR} ${DIST_DIR} ${VIEWS}

assets_scripts: assets_base
	@@${BUILD_DIR}/compile_scripts.sh ${SRC_DIR} ${DIST_DIR} ${SCRIPTS}

assets_styles: assets_base
	@@${BUILD_DIR}/compile_styles.sh ${SRC_DIR} ${DIST_DIR} ${STYLES}

assets_files: assets_base
	@@${BUILD_DIR}/copy_resources.sh ${SRC_DIR} ${DIST_DIR} ${RESOURCES}

clean: 
	@@rm -rf ${DIST_DIR}

.PHONY: welcome clean assets_views assets_scripts assets_styles assets_files
