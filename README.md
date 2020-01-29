# <a href="https://www.xilinx.com/products/design-tools/vitis/vitis-ai.html" target="_blank">Vitis-AI<a/> Xilinx’s development platform for AI inference
Tutorial of implementing custom neural network on custom board (ZCU106)

## Prerequisite
* OS Linux Ubuntu 16.04 <a href="http://releases.ubuntu.com/16.04/" target="_blank">link</a>
* Xilinx Vitis 2019.2 or newer <a href="https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/vitis.html" target="_blank">link</a>
* Petalinux tools (same version as Vitis) <a href="https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html" target="_blank">link</a>
* Download <a href="https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/embedded-design-tools.html" target="_blank">Board Support Packages<a/>  
* Clone repositories (same branch as version of Vitis)
	```
  git clone https://github.com/Xilinx/Vitis-AI
  git clone https://github.com/Xilinx/XRT
  git clone https://github.com/Xilinx/Vitis_Accel_Examples
	```
* Install XRT (or compile downloaded XRT repo) <a href="https://www.xilinx.com/html_docs/xilinx2019_2/vitis_doc/Chunk1674708719.html?hl=xrt" target="_blank">link</a>
  * Python version error <a href="https://www.xilinx.com/support/answers/73055.html" target="_blank">link</a>
* <b>Optional</b>\
  Device tree compiler <a href="https://www.xilinx.com/support/documentation/ip_documentation/dpu/v3_1/pg338-dpu.pdf" target="_blank">guide<a/> 
	```
  sudo apt install device-tree-compiler
	```
## Vitis Install/launch
  
## Create custom design
Based on <a href="https://www.xilinx.com/html_docs/xilinx2019_2/vitis_doc/Chunk1854106950.html#ariaid-title4" target="_blank">link<a/>\
Additional steps on <a href="https://www.xilinx.com/html_docs/xilinx2019_2/vitis_doc/Chunk2002802310.html#mik1571785455583" target="_blank">link<a/>
1. Create project for your board\
  Add files to project dir (TODO: file names)
2. Add all components in guide, rename parts/signals, setup platform (TODO: TCL scrypt)
3. Synthetize design (no bitstream required)  
  ```
  TODO: genarate TCL scrypt
  ```
4. Save hardware info (*.XSA)

## Setup Petalinux
Based on <a href="https://www.xilinx.com/html_docs/xilinx2019_2/vitis_doc/Chunk375818786.html#hog1570652702356" target="_blank">link<a/>
* Create project from BSP file 
  ```
  petalinux-create -t project -s <path-to-bsp>
  cd petalinux
  petalinux-config --get-hw-description=../<exported_dir_with_XSA>
  ```
* Add dir `XRT/src/platfrom/recipes-xrt` to `petalinux/project-spec/meta-user/recipes-xrt`
* Complete tutorial

## Create Platform
Based on <a href="https://www.xilinx.com/html_docs/xilinx2019_2/vitis_doc/Chunk356017304.html#jvn1570652701832" target="_blank">link<a/>
* platform info\
  TODO: image right platfrom

## Generate SD card
* Generate bitstream
* File for SD card

## Compile network
* Run docker
* Generater dpu info file
  ```
  dle /DPU-TRD/prj/Vitis/binary_container_1/sd_card/design_1.hwh
  ```
  and rename it to `ZCU106.dcf`
  
* Create board info file `ZCU106.json` for compiler
  ```
  {
  	"target": "dpuv2",
	"dcf": "ZCU106.dcf",
	"cpu_arch": "arm64"
  }
  ```


## Create application
