# leetcodee----3350
Adjacent Increasing Subarrays Detection II
//code in C++
class Solution {
public:
    bool canFindTwoIncreasingSubarrays(vector<int>& inc,int k,int n){
        for (int i=0;i+2 * k-1 < n;++i){
            if(inc[i]>=k && inc[i+k] >=k){
                return true;
            }
        }
        return false;
    }

    int maxIncreasingSubarrays(vector<int>& nums) {
        int n=nums.size();
        vector<int> inc(n,1);

        for(int i=n-2;i>=0;--i){
            if(nums[i]< nums[i+1]){
                inc[i]= inc[i+1] + 1;
            }
        }
        int left=1,right=n/2,result=0;
        while(left<=right){
            int mid=left+(right-left)/2;
            if(canFindTwoIncreasingSubarrays(inc,mid,n)){
                result=mid;
                left=mid+1;
            }else{
                right=mid-1;
            }
        }
        return result;
    }
};
