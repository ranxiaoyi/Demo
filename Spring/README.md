#二分法查找，如果数组中有多个相同的值，按照leftOrRight参数来判断返回最左还是最右的
private static int binarySearch(int[] arr, int key, boolean leftOrRight) {
        int low = 0;
        int high = arr.length - 1;
        int index = -1;
        out:
        while (low <= high) {
            int middle = low + ((high - low) >>> 1);
            if (arr[middle] < key) {
                low = middle + 1;
            } else if (arr[middle] > key) {
                high = middle - 1;
            } else if (arr[middle] == key) {
//                index = middle;
//                if (leftOrRight) {
//                    low = middle + 1;
//                } else {
//                    high = middle - 1;
//                }
                if (leftOrRight) {
                    for (int i = middle; i < high - 1; i++) {
                        if (arr[i] < arr[i + 1]) {
                            index = i;
                            break out;
                        }
                    }
                } else {
                    for (int i = low; i > 0; i--) {
                        if (arr[i] > arr[i - 1]) {
                            index = i;
                            break out;
                        }
                    }
                }
            }
        }
        return index;
    }
