public class MaximumSumPath {
    public static int maxSumPath(int[] X, int[] Y) {
        int m = X.length;
        int n = Y.length;

        int i = 0, j = 0;
        int sumX = 0, sumY = 0, maxSum = 0;

        while (i < m && j < n) {
            if (X[i] < Y[j]) {
                sumX += X[i++];
            } else if (X[i] > Y[j]) {
                sumY += Y[j++];
            } else { // When elements are equal, consider maximum sum path till now and add current element
                maxSum += Math.max(sumX, sumY);
                maxSum += X[i];
                sumX = 0;
                sumY = 0;
                i++;
                j++;
            }
        }

        // Add remaining elements of X[] and Y[]
        while (i < m) {
            sumX += X[i++];
        }
        while (j < n) {
            sumY += Y[j++];
        }

        // Add maximum sum of remaining paths
        maxSum += Math.max(sumX, sumY);

        return maxSum;
    }

    public static void main(String[] args) {
        int[] X = {3, 6, 7, 8, 10, 12, 15, 18, 100};
        int[] Y = {1, 2, 3, 5, 7, 9, 10, 11, 15, 16, 18, 25, 50};

        System.out.println("Maximum sum path: " + maxSumPath(X, Y));
    }
}
