# uw_cs540_2024_notes
This is my understand of the introductory course cs540 @ uw madison
Welcome to correct any mistakes

Lecture 1：

# N-gram Model

  我们一般把一个句子里的每一个单词当作一个token（字符单元的集合的表示）
  <img width="500" alt="Screenshot-2024-05-14-at-3 05 41PM" src="https://github.com/BaichengRen/uw_cs540_2024_notes/assets/171110441/8b871d1a-2f10-4793-8997-fb5b07aabe81">
  
  一个由d个单词组成的句子可以表示为一个由d个token组成的合集 (w1,w2,w3, ... ,wd)
  新单词 wt 的概率 P（wt | wt-1, wt-2, wt-3 .... w1,w0) 是指在w0,w2,w2 ..., wt-1 都出现的情况下，wt出现的概率
  当出现预测一串单词过后的下一个单词的时候我们需要考虑前面出现的所有单词。 当然这个是最理想的情况，因为这样的模型会很复杂，而且越往前面的单词对于新单词的预测的影响微乎其微，所以实际应用中我们只会考虑前面一部分单词。
  这引出了N-gram 的概念。 
  N-gram 假设 P（wt | wt-1, wt-2, wt-3 .... w1,w0) = P（wt | wt-1, wt-2, wt-3 .... wt-N+1)， 换一句话说假设只有前面N-1个单词会影响新的单词
  
# Unigram Model
  在N-gram Model的框架下 Unigram 会很好理解，那就是所有单词的的选择都是独立的。前面的任何单词都不会影响新的单词
  P（wt | wt-1, wt-2, wt-3 .... w1,w0) = P（wt)

# Maximum Likelihood Estimation
  这个是考虑抽样中的概率，P(wt) 即为wt出现的频率， 如 a a a b b 中样本中，P（a) = 3/5
