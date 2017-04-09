# statistics_simple
데이터 사이언스, 데이터마이닝에서 요구되는 통계학적 기본지식들을 python 구현과 함께 나타내었다.

1.데이터 시각화
- matplotlib

![img1](/img/img1.png)

![img2](/img/img2.png)

2. 평균(mean), 중앙값(median), 분위(quantile), 최빈값(mode)
- 평균은 데이터가 나태는 값들의 전체 합을 데이터의 수로 나눈것을 의미한다.
- 중앙값은 전체 데이터를 정렬하였을때 정 가운데 인덱스가 나타내는 값을 의미한다
- 분위,p가 주어졌을 때. 이에대한 분위는 데이터를 정렬하고 데이터의 수 * p 에 해당하는 인덱스가 나타내는 값을 의미한다.
- 최빈값은 데이터가 나타내는 값들 중 가장 빈번하게 나타난 값을 의미한다.

평균은 데이터셋에 존재하는 각각의 값의 변화에 민감하다. 예를들어, 데이터셋의 최댓값이 100에서 10000으로 변경되었다면 평균값은 변경되나 중앙값은 변동하지 않는다또한, 평균값은 Noise에 대해서 상당히 민감한데, 상위2%가 전체 데이터의 평균을 dominant할 수 있다는 뜻이다. 이에 대한 해결책으로 데이터셋에대한 평균값을 구하고자 할 때 상위2%, 하위2%에 해당하는 데이터를 무시하고 나머지 데이터만을 통해 평균값을 구하는 방법이 있다.

<pre><code>
def median(data):
    n = len(data)
    sorted_v = sorted(data)
    middle = n // 2
    if n % 2 == 1:
        return data[middle]
    else:
        left = middle-1
        right = middle
        return (data[left] + data[right]) / 2
</code></pre>

<pre><code>
def quantile(x,p):
    p_index = int(len(x) * p)
    return sorted(x)[p_index]
</code></pre>

<pre><code>
def mode(x):
    counts = Counter(x) # key : 값 , value : count
    #print(counts)
    max_count = max(counts.values())
    #print(max_count)
    return [ key for key,count in counts.items() if count == max_count]
</code></pre>
