# exponential_curve_fitting
import numpy as np
# curve-fit() function imported from scipy
from scipy.optimize import curve_fit
from matplotlib import pyplot as plt
x = np.array([-5.0003,-4.0003,-3.0003,-2.0003,-1.0003,0.1994,0.397,0.567,0.658,0.73,0.73,0.784,0.805,0.851,0.836,0.82, 0.885,0.946,0.885,0.9,0.97,1.02,0.98,1.09,1.12])
y = np.array([0.000064, 0.000064, 0.000064, 0.000064, 0.000064, 0.00013, 0.00067, 0.00702, 0.0302, 0.0614, 0.1, 0.131, 0.174, 0.213, 0.244, 0.354, 0.556, 0.649, 0.769, 0.872, 1.070, 1.272, 1.493, 1.683, 1.889])
a = 0.7
b = 1.4 * (10 ^ -23)
def func(x, b, a):
    return a*np.exp(b*x-1)

param, param_cov = curve_fit(func, x, y)
print("function coefficients:")
print(param)
print("Covariance of coefficients:")
print(param_cov)
# ans stores the new y-data according to
# the coefficients given by curve-fit() function
ans = (param[0] * (np.sin(param[1] * x)))
plt.plot(x, y, 'o', color ='red', label ="data")
plt.plot(x, ans, '--', color ='blue', label ="optimized data")
plt.legend()
plt.show()
