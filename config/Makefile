# For local zmk build use

# Assume you hava zmk-config and zmk in a same dir
MAKE_DIR = ../../zmk/app

CONFIG_DIR= $(PWD)

BUILD_DIR = $(CONFIG_DIR)/build
BUILD_LEFT_DIR = $(BUILD_DIR)/left
BUILD_RIGHT_DIR = $(BUILD_DIR)/right
RELEASE_DIR = $(CONFIG_DIR)/release

# BOARD = nrfmicro_13
BOARD = nice_nano_v2

SHIELD_LEFT = owl_left 
SHIELD_RIGHT = owl_right 

.PHONY: build left right clean 

build: left right

left:
	cd $(MAKE_DIR) && west build -d $(BUILD_LEFT_DIR) -b $(BOARD) -- -DSHIELD=$(SHIELD_LEFT) -DZMK_CONFIG=$(PWD)
	cp $(BUILD_LEFT_DIR)/zephyr/zmk.uf2 $(RELEASE_DIR)/left.uf2

right:
	cd $(MAKE_DIR) && west build -d $(BUILD_RIGHT_DIR) -b $(BOARD) -- -DSHIELD=$(SHIELD_RIGHT) -DZMK_CONFIG=$(PWD)
	cp $(BUILD_RIGHT_DIR)/zephyr/zmk.uf2 $(RELEASE_DIR)/right.uf2

copy:
	scp -r release localmac:~/Downloads

clean:
	rm -rf $(BUILD_DIR) $(RELEASE_DIR)
	mkdir ./build ./build/left ./build/right ./release
