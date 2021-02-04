# 算法————滑动窗口
可以用来解决一些查找满足一定条件的连续区间的性质（长度等）的问题。由于区间连续，因此当区间发生变化时，它可以将嵌套的循环问题，转换为单循环问题，样便减少了重复计算，降低了时间复杂度。往往类似于“请找到满足xx的最x的区间（子串、子数组）的xx”这类问题都可以使用该方法进行解决。
例1.给定一个整数数组，计算长度为 'k' 的连续子数组的最大总和。
  输入：a[]={100,200,700,400}，k=2
  输出:1100
  解释：700+400=1100
暴力法：
C++:
double func(vector<int>& a,int k)
{
  int n=a.size();
  int sum=0;
  int maxsum=0;
  for(int i=0;i<n-1;i++)
  {
      for(int j=i+1;j<n;j++)
      {
          sum=a[i]+a[j];
          maxsum=max(sum,maxsum);
      }
  }
  return (double)maxsum;
}
Java:
时间复杂度：O(k*n)
滑动窗口法：
当k=2时，设置窗口大小为2，窗口里的值的和保存在一个变量，通过不断的往右滑算出每个窗口的值，并与保存的最大值比较，滑到最右端为止
(100 200) 700 400
100 (200 700) 400
100 200 (700 400)
C++:
double func(vector<int>& nums, int k) {
  int sum=0;
  int n=nums.size();
  for(int i=0;i<k;i++)
      sum=sum+nums[i];
      int maxsum=sum;
      for(int i=k;i<n;i++)
      {
          sum=sum-nums[i-k]+nums[i];
          maxsum=max(maxsum,sum);
      }
      return (double)maxsum;
  }
};
如LeetCode209、643
