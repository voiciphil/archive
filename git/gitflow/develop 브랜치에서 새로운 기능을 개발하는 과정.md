# gitflow-tutorial

### develop 브랜치에서 새로운 기능을 개발하는 과정

```bash
(develop) $ git pull origin develop	
```
2. feature 브랜치를 생성한다.
```bash
(develop) $ git checkout -b feature
```
3. 작은 기능으로 쪼개서 개발한다. 
```bash
(feature) $ git commit -m "..."
```
4. 원격 develop 브랜치 변경사항을 pull 하고 feature 브랜치를 develop 브랜치에 rebase 하여 conflict를 해결한다.
```bash
(feature) $ git checkout develop
(develop) $ git pull origin develop
(develop) $ git rebase develop feature # feature 브랜치로 checkout 된다.
```
5. feature 브랜치를 원격 저장소로 push 한다.
```bash
(feature) $ git push origin feature
```
> 9번에서 다시 돌아왔으면 push가 되지 않을 수 있다.   
> 이때 다음 두 가지 방법 중 하나를 선택한다.
>
> 1. -f 옵션을 사용하여 강제 push 한다.
> ```bash
> (feature) $ git push -f origin feature
> ```
> 2. 원격 feature 브랜치를 지우고 다시 push 한다.
> ```bash
> (feature) $ git push origin :feature
> (feature) $ git push origin feature
> ```

6. github 에서 원격 develop 브랜치에 PR을 날린다.
7. github 에서 원하는 방식을 사용해 merge 한다.
8. 원격 develop 브랜치에서 merge 된 결과를 pull 하고 원격 로컬 모두 feature 브랜치를 삭제한다. 
```bash
(develop) $ git pull origin develop
(develop) $ git branch -D feature # 로컬 브랜치 강제 삭제
(develop) $ git push origin :feature # 원격 브랜치 삭제
```
9. merge 되지 않으면 3번부터 다시 시작한다.

### 참고 자료

* [Git 협업 가이드](https://velog.io/@jinuku/Git-%ED%98%91%EC%97%85-%EA%B0%80%EC%9D%B4%EB%93%9C)
* [Git Rebase 활용하기](https://velog.io/@godori/Git-Rebase)