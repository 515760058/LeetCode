class Solution {
public:
    int minArray(vector<int>& numbers) {
        return *min_element(numbers.begin(), numbers.end());
    }
};