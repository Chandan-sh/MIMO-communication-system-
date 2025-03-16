# simulation.py

import numpy as np
from transmitter import generate_data, modulate_data, mimo_encoding
from channel import generate_mimo_channel, transmit_through_channel, add_awgn_noise
from receiver import zero_forcing_detection, demodulate_data

# Simulation parameters
num_symbols = 1000
num_tx = 2
num_rx = 2
snr_db = 20

# Transmitter
data = generate_data(num_symbols)
modulated_data = modulate_data(data)
mimo_encoded_data = mimo_encoding(modulated_data, num_tx)

# Channel
channel = generate_mimo_channel(num_tx, num_rx)
received_signal = transmit_through_channel(channel, mimo_encoded_data)
noisy_signal = add_awgn_noise(received_signal, snr_db)

# Receiver
detected_signal = zero_forcing_detection(channel, noisy_signal)
demodulated_data = demodulate_data(detected_signal)

# Performance analysis
ber = np.sum(data != demodulated_data.flatten()) / num_symbols
print(f"Bit Error Rate (BER): {ber}")
