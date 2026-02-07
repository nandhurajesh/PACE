# PACE
only for education process the code is copied from leetcode 

Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:
programing language:C++
Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.


class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
        bool row[9][9] = {false};
        bool col[9][9] = {false};
        bool box[9][9] = {false};
        
        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {
                if (board[i][j] == '.') continue;
                
                int num = board[i][j] - '1';          // 0 to 8
                int b = (i / 3) * 3 + (j / 3);        // box index
                
                if (row[i][num] || col[j][num] || box[b][num])
                    return false;
                
                row[i][num] = col[j][num] = box[b][num] = true;
            }
        }
        return true;
    }
};
