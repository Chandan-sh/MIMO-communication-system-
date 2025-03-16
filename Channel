# channel.py

import numpy as np

def generate_mimo_channel(num_tx, num_rx):
    """Generate a MIMO channel matrix with Rayleigh fading."""
    return (np.random.randn(num_rx, num_tx) + 1j * np.random.randn(num_rx, num_tx)) / np.sqrt(2)

def transmit_through_channel(channel, data):
    """Transmit data through the MIMO channel."""
    return np.dot(channel, data)

def add_awgn_noise(signal, snr_db):
    """Add AWGN noise to the signal."""
    snr_linear = 10 ** (snr_db / 10)
    noise_power = np.mean(np.abs(signal) ** 2) / snr_linear
    noise = np.sqrt(noise_power / 2) * (np.random.randn(*signal.shape) + 1j * np.random.randn(*signal.shape))
    return signal + noise

# Example usage
if __name__ == "__main__":
    channel = generate_mimo_channel(2, 2)
    data = np.random.randn(2, 500) + 1j * np.random.randn(2, 500)
    received_signal = transmit_through_channel(channel, data)
    noisy_signal = add_awgn_noise(received_signal, 20)
    print(noisy_signal)
