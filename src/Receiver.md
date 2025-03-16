 # Receiver.py

        import numpy as np
        
        def zero_forcing_detection(channel, received_signal):
        
            #Apply Zero Forcing detection to the received signal.
            channel_inv = np.linalg.inv(channel)
            return np.dot(channel_inv, received_signal)
        
        def demodulate_data(detected_signal, modulation_scheme='BPSK'):
        
            #Demodulate the detected signal.
            if modulation_scheme == 'BPSK':
                return (np.real(detected_signal) > 0).astype(int)
                
            # Add other demodulation schemes as needed
            raise ValueError("Unsupported modulation scheme")
        
        # Example usage
        if __name__ == "__main__":
            channel = (np.random.randn(2, 2) + 1j * np.random.randn(2, 2)) / np.sqrt(2)
            data = np.random.randn(2, 500) + 1j * np.random.randn(2, 500)
            received_signal = np.dot(channel, data)
            detected_signal = zero_forcing_detection(channel, received_signal)
            demodulated_data = demodulate_data(detected_signal)
            print(demodulated_data)
