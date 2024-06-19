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
  
# Bigram Model
  与之前的类似 P（wt | wt-1, wt-2, wt-3 .... w1,w0) = P（wt | wt-1),新的单词只需要考虑上一个单词 注意计算 Maximum Likelihood时也是 wt在wt-1之后出现的次数/wt-1 出现的次数

# Transition Matrix
  把上一个Bigram的概率写入一个matrix里 P（j|i）= 在matrix中 row i column x 的值

# Trigram Model
  道理同上，不过值得注意的是Laplace smoothing
  Laplace smoothing指的是给所有可能性都给予一些很小的概率使他们不为0
  比如说在aaabb 中，unigram, 有 3个a,2个b, 0个c a的概率为3/5 c的概率为0。 这种情况下我们下一个单词永远不可能是c。但是我们要保留这种可能性，就好比说“吃”这个单词后面很少出现“21号混凝土”，但是不是不可能。所以在计算的时候要修正一下
  这引入了Laplace smoothing，我们考虑4个a,3个b, 1个c，这样虽然c的概率很小1/8,但是还是保留了一定的概率
  
