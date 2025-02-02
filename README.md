# Antenna-representation-using-MATLAB-for-N-antenna-at-10-GHz

-Number of antennas = N (variable)
- Desired angle of arrival = 30ο (measured from a line perpendicular to the array)
- The carrier frequency = f =10 GHz
- The distance, d, between adjacent antennas in the array is uniform. 𝑑 =
𝜆, 𝜆/2, and 3𝜆/2
- Each UE has a single omnidirectional antenna, and they are in the far field of the array.

MATLAB code:
```
f = 10e9; % Carrier frequency in Hz
lambda = 3e8 / f; % Wavelength in meters
k = 2 * (pi / lambda);
theta = 30; % Angle of arrival in degrees
% Define N values
N_values = [2, 4, 6, 8];
% Define distances between adjacent antennas (d)
d_values = [lambda, lambda/2, 3*lambda/2];
% Define the angle range for calculation
phi = -1.5:0.001:1.5; % Angle range
% Calculate Array Factor for each combination of N and d
for N = N_values
    for d = d_values
        % Calculate the Array Factor for the given angle range, N, and d
        AF = zeros(size(phi));
        delta_phi = (2 * pi * d * sin(theta)) / lambda;
        for i = 1:length(phi)
            AF_phi = k * d * sin(theta) * sin(phi(i)) + delta_phi;
            AF(i) = (1/N) * abs(sin(N * AF_phi / 2) / sin(AF_phi / 2));
        end
        % Plot the Array Factor
        figure;
        plot(phi, AF);
        title(['Array Factor for N = ' num2str(N) ', d = ' num2str(d/lambda) '\lambda']);
        xlabel('Phase/rad');
        ylabel('Array Factor');
        grid on;
    end
end
```
Output

![image](https://github.com/user-attachments/assets/86d7d32f-19b4-4bb2-b938-5d1f0c171586)

![image](https://github.com/user-attachments/assets/017b8766-d30a-4e33-9487-04a3d4246a00)

![image](https://github.com/user-attachments/assets/3f530454-0f26-48bb-8e36-7ef66e6239cf)
