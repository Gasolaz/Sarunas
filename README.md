# Sarunas
public static int intersectingDiscs(int[] A) {
        // 0 1 2 3 4 5
        // 1 5 2 1 4 0 = 11           1 1 1
        // -1 -4 0 2 0 5              -1 0 1
        // 1 6 4 4 8 5                1 2 3
        long[] min = new long[A.length];
        long[] max = new long[A.length];
        int intersect = 0;
        for (int i = 0; i < A.length; i++) {
            min[i] = i - (long) A[i];
            max[i] = i + (long) A[i];
        }
//        for (int i = 0; i < A.length; i++) {
//            System.out.println(min[i]);
//            System.out.println(max[i]);
//        }
        for (int i = 0; i < A.length - 1; i++) {
            for (int j = i + 1; j < A.length; j++) {
                if ((min[i] <= max[j] && max[i] >= min[j])) {
                    intersect++;
                    if (intersect > 10_000_000) {
                        return -1;
                    }
                }
            }
        }
        return intersect;
    }
