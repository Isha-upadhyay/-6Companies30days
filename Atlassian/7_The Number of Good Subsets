class Solution {
public:
    vector<int> primes = {2,3,5,7,11,13,17,19,23,29};
    long mod = 1e9 + 7;
    int createMask(int num) {
        int mask = 0,curr;
        while(num != 1) {
            for(int i = 0; i < primes.size(); i++){
                if(num % primes[i] == 0){
                    curr = (1<<i);
                    if((mask & curr) != 0) return -1;
                    mask |= curr;
                    num /= primes[i];
                    break;
                }
            }
        }
        return mask;
    }

    int helper(int i, vector<vector<int>> &dp, vector<int> &cnt, vector<int> &m, int mask){
        if(i == 31) 
            //if no number is taken then return 0
            return (mask != 0);
        /*check if either number does not exist in input or 
        if the number is bad due to repeating prime factor*/
        if(dp[i][mask] != -1) return dp[i][mask];
        if(cnt[i] == 0 || m[i] == -1) return dp[i][mask] = helper(i+1,dp,cnt,m,mask) % mod;

        //typical knapsack (take | not-take)
        long long res = 0;
        if((mask & m[i]) == 0) res = ((long long)helper(i+1,dp,cnt,m,mask | m[i]) * cnt[i]) % mod;
        res = (res + helper(i+1,dp,cnt,m,mask)) % mod;
        return dp[i][mask] = res % mod;
    }

    int numberOfGoodSubsets(vector<int>& nums) {
        vector<int> primeMask(31,0);
        vector<int> cnt(31,0);
        vector<vector<int>> dp(31,vector<int>((1<<11)-1,-1));
        for(auto &i : nums) cnt[i]++;

        for(int i = 1; i < 31; i++)
            primeMask[i] = createMask(i);
        // cout<<"abfkafkafba";
        //set 1's mask as bad as it can be added in any good subset
        primeMask[1] = -1; 

        long long res = helper(2,dp,cnt,primeMask,0);
        long long op = 1;
        //all combination sets of 1
        for(int i = 0 ; i < cnt[1]; i++) op = (op * 2) % mod;
        return (res * op) % mod;
    }
};
