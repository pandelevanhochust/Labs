/*
 * 7seg.cpp
 *
 *  Created on: Mar 20, 2025
 *      Author: TrungNL
 */
#include "main.h"
#include "7seg.h"
#include "stm32f4xx_hal.h"

int DisplayHigh = 0;
int DisplayLow = 0;
int pos = 0;

unsigned char Mask[] = {
	0b00111111, // 0
	0b00000110, // 1
	0b01011011, // 2
	0b01001111, // 3
	0b01100110, // 4
	0b01101101, // 5
	0b01111101, // 6
	0b00000111, // 7
	0b01111111, // 8
	0b01101111, // 9
	0b01110111, // A
	0b01111100, // B
	0b00111001, // C
	0b01011110, // D
	0b01111001, // E
	0b01110001  // F
};
void Set7SegHexByte(unsigned char val)
{
	DisplayHigh = (val >> 4) & 0x0F;
	DisplayLow = val & 0x0F;
	pos = 0;
}

void Run7SegDisplay()
{
	unsigned char val;
	pos++;

	HAL_GPIO_WritePin(PORT_7SEG_CONTROL1, PIN_7SEG_CONTROL1, GPIO_PIN_RESET);
	HAL_GPIO_WritePin(PORT_7SEG_CONTROL0, PIN_7SEG_CONTROL0, GPIO_PIN_RESET);

	if (pos & 0x1)
		val = Mask[DisplayLow];  // digit bên phải
	else
		val = Mask[DisplayHigh]; // digit bên trái

	if (val & 0x80) HAL_GPIO_WritePin(PORT_7SEG_P, PIN_7SEG_P, GPIO_PIN_SET); else HAL_GPIO_WritePin(PORT_7SEG_P, PIN_7SEG_P, GPIO_PIN_RESET);
	if (val & 0x40) HAL_GPIO_WritePin(PORT_7SEG_G, PIN_7SEG_G, GPIO_PIN_SET); else HAL_GPIO_WritePin(PORT_7SEG_G, PIN_7SEG_G, GPIO_PIN_RESET);
	if (val & 0x20) HAL_GPIO_WritePin(PORT_7SEG_F, PIN_7SEG_F, GPIO_PIN_SET); else HAL_GPIO_WritePin(PORT_7SEG_F, PIN_7SEG_F, GPIO_PIN_RESET);
	if (val & 0x10) HAL_GPIO_WritePin(PORT_7SEG_E, PIN_7SEG_E, GPIO_PIN_SET); else HAL_GPIO_WritePin(PORT_7SEG_E, PIN_7SEG_E, GPIO_PIN_RESET);
	if (val & 0x08) HAL_GPIO_WritePin(PORT_7SEG_D, PIN_7SEG_D, GPIO_PIN_SET); else HAL_GPIO_WritePin(PORT_7SEG_D, PIN_7SEG_D, GPIO_PIN_RESET);
	if (val & 0x04) HAL_GPIO_WritePin(PORT_7SEG_C, PIN_7SEG_C, GPIO_PIN_SET); else HAL_GPIO_WritePin(PORT_7SEG_C, PIN_7SEG_C, GPIO_PIN_RESET);
	if (val & 0x02) HAL_GPIO_WritePin(PORT_7SEG_B, PIN_7SEG_B, GPIO_PIN_SET); else HAL_GPIO_WritePin(PORT_7SEG_B, PIN_7SEG_B, GPIO_PIN_RESET);
	if (val & 0x01) HAL_GPIO_WritePin(PORT_7SEG_A, PIN_7SEG_A, GPIO_PIN_SET); else HAL_GPIO_WritePin(PORT_7SEG_A, PIN_7SEG_A, GPIO_PIN_RESET);

	if (pos & 0x1)
		HAL_GPIO_WritePin(PORT_7SEG_CONTROL1, PIN_7SEG_CONTROL1, GPIO_PIN_SET);  // digit right
	else
		HAL_GPIO_WritePin(PORT_7SEG_CONTROL0, PIN_7SEG_CONTROL0, GPIO_PIN_SET);  // digit left
}


