# -EventQueue-
#include "mbed.h"

InterruptIn button(USER_BUTTON);
EventQueue *queue = mbed_event_queue();

// Function to print the button press message
void print_message() {
    printf("Button pressed\n");
}

// Function to be called when the button is pressed
void onButtonPress() {
    queue->call(&print_message);
}

int main() {
    button.rise(&onButtonPress);

    while (true) {
        ThisThread::sleep_for(1000ms);
    }
}
