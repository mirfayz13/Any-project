# Any-project
class CloneRange:
    def __init__(self, start, stop = None, step = 1):
        if stop is None:
            self.stop = start
            self.start = -step
            self.step = step
        else:
            self.start = start - step
            self.stop = stop
            self.step = step

    def __iter__(self):
        print("Call iter ")
        return self

    def __next__(self):
        if self.start < self.stop and self.step > 0:
            print("Start next")
            self.start += self.step
            if self.start >= self.stop:
                raise StopIteration
            return self.start
        if self.start > self.stop and self.step < 0:
            print("Start next")
            self.start += self.step
            if self.start <= self.stop:
                raise StopIteration
            return self.start

for i in CloneRange(10):
    print(i)




import time
from datetime import datetime

def task_1(x):
    time.sleep(1)
    return x ** 2

def task_2(x):
    time.sleep(1)
    return x ** 3

def task_3(x):
    time.sleep(1)
    return x ** 4

def main(x):
    yield task_1(x)
    yield task_2(x)
    yield task_3(x)

if __name__ == "__main__":
    print(datetime.now().time())
    for i in main(5):
        print(i)
    print(datetime.now().time())
