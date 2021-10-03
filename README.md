images https://mendel-linux.org/images/enterprise/


SD-Karte auf Mac erstellen
* sudo diskutil unmount /dev/disk3s1
* sudo dd bs=1m if=/<path>/<filename>.img of=/dev/disk3

on mac:
* own python venv
* pip install mendel-development-tool
* connect with usb 1st stime to create keys
* if not possible on mac 
	* connect with windows pc and get generated key from there
	* copy key on mac to  <home>/.config/mdt/keys/mdt.key

mdt commands (in shell)
* mdt devices
* mdt shell

connect with terminal
	* cd .ssh 
	* cp ../.config/mdt/keys/mdt.key ./id_rsa
	* chmod 600 id_rsa 
	* ssh mendel@coral

in coral shell:
* sudo shutdown now # shutdown. do not power off before !
* nmtui  # config
* nmcli connection show
* free -m  # check ram
* cat /etc/mendel_version # check version
* cat /sys/class/thermal/thermal_zone0/temp  # check temperature threshold

update
* sudo apt-get update
* sudo apt-get dist-upgrade

python / jupyter
* install
	* sudo apt-get install python3-dev
	* sudo apt-get install libffi-dev
	* pip3 install jupyter
	* sudo apt-get install libjpeg-dev zlib1g-dev # maybe nedded for for matplotlib
* run jupyter
	* jupyter notebook --no-browser --ip=0.0.0.0 --NotebookApp.token=''




demos:
* edgetpu_demo --stream
* packages to play with
	* mkdir coral && cd coral
	* git clone https://github.com/google-coral/pycoral.git
	* cd pycoral
	* bash examples/install_requirements.sh classify_image.py
	* python3 examples/classify_image.py \
		--model test_data/mobilenet_v2_1.0_224_inat_bird_quant_edgetpu.tflite \
		--labels test_data/inat_bird_labels.txt \
		--input test_data/parrot.jpg
