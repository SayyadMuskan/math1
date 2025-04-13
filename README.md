# math1

def calculate_mean(data):
    total = 0
    count = 0
    for value in data:
        total += value
        count += 1
    return total / count

def calculate_covariance(x, y, mean_x, mean_y):
    cov = 0
    for i in range(len(x)):
        cov += (x[i] - mean_x) * (y[i] - mean_y)
    return cov

def calculate_variance(data, mean):
    var = 0
    for value in data:
        var += (value - mean) ** 2
    return var

def calculate_correlation(x, y):
    mean_x = calculate_mean(x)
    mean_y = calculate_mean(y)
    cov_xy = calculate_covariance(x, y, mean_x, mean_y)
    var_x = calculate_variance(x, mean_x)
    var_y = calculate_variance(y, mean_y)
    correlation = cov_xy / ((var_x ** 0.5) * (var_y ** 0.5))
    return correlation

def calculate_regression(x, y):
    mean_x = calculate_mean(x)
    mean_y = calculate_mean(y)
    cov_xy = calculate_covariance(x, y, mean_x, mean_y)
    var_x = calculate_variance(x, mean_x)
    m = cov_xy / var_x
    b = mean_y - m * mean_x
    return m, b

x_input = input("Enter values of X separated by space: ")
y_input = input("Enter values of Y separated by space: ")

x = [float(i) for i in x_input.strip().split()]
y = [float(i) for i in y_input.strip().split()]

if len(x) != len(y):
    print("Error: X and Y must have the same number of elements.")
else:
    mean_x = calculate_mean(x)
    mean_y = calculate_mean(y)
    correlation = calculate_correlation(x, y)
    m, b = calculate_regression(x, y)

    print("\nMean of X:", mean_x)
    print("Mean of Y:", mean_y)
    print("Correlation Coefficient:", correlation)
    print("Linear Regression Equation: y =", m, "* x +", b)

    predict_input = input("Enter a value of x to predict y (or press Enter to skip): ")
    if predict_input.strip() != "":
        new_x = float(predict_input)
        predicted_y = m * new_x + b
        print("Predicted y for x =", new_x, "is", predicted_y)


