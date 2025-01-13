class Solution {
public:
    int findLength(vector<int>& A, vector<int>& B) {
        int ans = 0;
        vector<vector<int>> memo(A.size() + 1, vector<int>(B.size() + 1, 0));
        
        for (int i = A.size() - 1; i >= 0; --i) {
            for (int j = B.size() - 1; j >= 0; --j) {
                if (A[i] == B[j]) {
                    memo[i][j] = memo[i + 1][j + 1] + 1;
                    ans = max(ans, memo[i][j]);
                }
            }
        }
        return ans;
    }
};
