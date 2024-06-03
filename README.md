# hi
###### mebbe
```
def bernstein_poly(i,n,t):
            return comb(n,i)*(t**(n-i))*(1-t)**i
def bezeier_curve(points, nTimes=100):
    nPoints = len(points[0])
    xPoints = points[0]
    yPoints = points[1]
    t = np.linspace(0.0, 1.0, nTimes)
    poly_arr = np.array([bernstein_poly(i, nPoints-1,t) for i in range(0, nPoints)])
    xvals = np.dot(xPoints, poly_arr)
    yvals = np.dot(yPoints, poly_arr)
    return np.array(xvals[::-1]), np.array(yvals[::-1])
fit = bezeier_curve(path)
def bezier_derivative(points, nTimes=100):
    nPoints = len(points[0])
    xPoints = points[0]
    yPoints = points[1]

    # Compute the control points for the derivative curve
    dXPoints = np.array([(nPoints - 1) * (xPoints[i + 1] - xPoints[i]) for i in range(nPoints - 1)])
    dYPoints = np.array([(nPoints - 1) * (yPoints[i + 1] - yPoints[i]) for i in range(nPoints - 1)])
    
    t = np.linspace(0.0, 1.0, nTimes)
    poly_arr = np.array([bernstein_poly(i, nPoints - 2, t) for i in range(0, nPoints - 1)])
    dxvals = np.dot(dXPoints, poly_arr)
    dyvals = np.dot(dYPoints, poly_arr)
    return np.array(dxvals[::-1]), np.array(dyvals[::-1])
dfit = bezier_derivative(path)
```