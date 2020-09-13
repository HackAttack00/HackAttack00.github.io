
class Solution {
    func challenge15(input: String) -> String {
        let words = input.split(separator: " ")
        let reversedWords = words.map {String($0.reversed())}
        
        return reversedWords.joined(separator: " ")
    }
}

let solution = Solution.init()
solution.challenge15(input: "Swift Coding Challenges")
