# justForSavingCode

import java.util.NoSuchElementException;
import java.lang.Integer;

public class MatrixIterator implements java.util.Iterator {

    private int[] array;
    private int cursor;

    MatrixIterator(int[][] matrix) {
        this.array = IteratorUtil.convertFromMatrixToArray(matrix);
        this.cursor = 0;
    }

    @Override
    public boolean hasNext() {
        return cursor < array.length;
    }

    @Override
    public Integer next() {
        if (hasNext()) {
            cursor++;
            return array[cursor - 1];
        } else {
            throw new NoSuchElementException();
        }
    }

    @Override
    public void remove() {
        throw new UnsupportedOperationException();
    }

}

class IteratorUtil {
    static int[] convertFromMatrixToArray(int[][] matrix) {
        int[] result = new int[getNumOfElements(matrix)];
        int count = 0;
        for (int[] array : matrix) {
            for (int i : array) {
                result[count] = i;
                count++;
            }
        }
        return result;
    }

    private static int getNumOfElements(int[][] matrix) {
        int size = 0;
        for (int[] i : matrix) {
            size += i.length;
        }
        return size;
    }
}
