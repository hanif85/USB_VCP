# USB VCP STM32

USB VCP make development more easy and can reduce hardware like rs232 in board that make impact reduce size of board and reduce cost.
This Example code is for easy use when use to send data from STM32 to PC from USB. 
Just add this in **main.c
'''C/C++
  int _write(int file, uint8_t *ptr, int len){
	static uint8_t rc = USBD_OK;
	do {
		rc = CDC_Transmit_FS((uint8_t *) ptr, len);
	}while (USBD_BUSY == rc);

	if (USBD_FAIL == rc) {
		return 0;
	}
	return len;
}
'''

and to send data just use **printf("hello data");
