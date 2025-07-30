#include <reg51.h>

#define SEGMENT P1
sbit DIGIT0 = P2^0;
sbit DIGIT1 = P2^1;
sbit DIGIT2 = P2^2;
sbit DIGIT3 = P2^3;
sbit DIGIT4 = P2^4;
sbit DIGIT5 = P2^5;
sbit BUZZER = P3^7;  // Buzzer connected to P3.7

// digits[] = {secU, secT, minU, minT, hrU, hrT}
unsigned char digits[6] = {9, 5, 9, 5, 2, 0}; // Start from 02:59:59

unsigned char code seg_code[10] = {
    0x3F, 0x06, 0x5B, 0x4F, 0x66,
    0x6D, 0x7D, 0x07, 0x7F, 0x6F
};

void show();
void delay_short(); 
void countdown();
void beep();

unsigned int second_counter = 0; // Used to delay 1 sec for real time

void main() {
    while (1) {
        show();          // Display time
        second_counter++;
        if (second_counter >= 83) { // Roughly 1 second (tune if needed)
            countdown();
            second_counter = 0;
        }
    }
}

void show() {
    SEGMENT = seg_code[digits[0]]; DIGIT0 = 0; delay_short(); DIGIT0 = 1;
    SEGMENT = seg_code[digits[1]]; DIGIT1 = 0; delay_short(); DIGIT1 = 1;
    SEGMENT = seg_code[digits[2]]; DIGIT2 = 0; delay_short(); DIGIT2 = 1;
    SEGMENT = seg_code[digits[3]]; DIGIT3 = 0; delay_short(); DIGIT3 = 1;
    SEGMENT = seg_code[digits[4]]; DIGIT4 = 0; delay_short(); DIGIT4 = 1;
    SEGMENT = seg_code[digits[5]]; DIGIT5 = 0; delay_short(); DIGIT5 = 1;
}

void delay_short() {
    unsigned int i;
    for (i = 0; i < 200; i++);
}


// Countdown logic with buzzer trigger after 10 sec
void countdown() {
    // Countdown logic
    if (digits[0]-- == 0) {
        digits[0] = 9;
        if (digits[1]-- == 0) {
            digits[1] = 5;
		if(digits[2]==0&&digits[3]==0){
			digits[0]=0;
			digits[1]=0;
			return;}
            if (digits[2]-- == 0) {
                digits[2] = 9;
                if (digits[3]-- == 0) {
                    digits[3] = 5;
			if(digits[4]==0){
				digits[3]=0;
				digits[2]=0;}
                    if (digits[4]-- == 0) {
                        digits[4] = 0;
                        if (digits[5]-- == 0) {
                            digits[5] = 0;
                        }
                    }
                }
            }
        }
    }
}
