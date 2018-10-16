---
layout: post 
title: "GitHub PullRequest를 통해 Code Review하기" 
date: 2018-08-10 20:00:00 +0900
category: dev
author: "huansuh"
tags: ["code_review", "github"]
---



# GitHub Pull Request를 통해 Code Review하기



Defind에 iOS 개발자 Joy가 합류했다.<br>**Welcome Joy!!! :)**



물론 나는 안드로이드 개발을 하고, joy는 ios를 개발하기 때문에 직접적으로 같은 코드를 가지고 작업하지는 않을 것 같다.<br>Backend, Android, iOS 다 따로따로 담당자 1인 개발 체제ㅜㅜ



그래도 '개발 문화가 좋다', '개발자로 성장할 수 있는 좋은 기회다'라는 이야기를 들을 수 있는 
개발팀을 꾸리고 싶은 욕심이 있었기 때문에 Code Review를 해보고 싶었다.



swift, object-c 경험이 부족하기 때문에 Syntax나 문법 관련되어 line by line으로 진행하는 방법 보다는
구조적이나 기존에 Android 개발 진행된 Logic 적인 부분 중심으로 진행할 것이다.<br>Joy도 관련된 방향에 긍정적으로 생각해 주어서 열심히 해봐야지… Thank you~



### Code Review를 통해 얻고자 하는 것

* Code 품질 및 성능 향상
* 개발자가 성장할 수 있는 개발 문화 확립
* Reviewer의 성장(내 iOS 공부) + Committer의 성장(Joy에게 조금이나마 도움이 될 수 있다면...)



## Code Review 방식

(Code Review 방식 + 전반적인 GitHub Workflow)

![github_workflow](/files/github_workflow.png)



1. **clone**

   - project를 clone하여 local directory에 생성한다.

   ```
   git clone https://github.com/{remote_account}/{repository_name}
   ```

   <br>

2. **checkout -b 'branch'**

   * 기능 구현을 위한 branch를 생성한다.

   ```
   git checkout -b 'branch_name'
   ```

   (Branch 생성)

   1. Trello 작업 등록
   2. Trello CardNumber*(Card detail > Share and more...)* 로 branch 생성

   ![trello_cardnumber](/files/trello_cardnumber.png)

3. **add / commit**

   - 코드 작성 후 작업한 내용을 commit한다.

   ```
   git status // 변경사항 확인
   git rm 'file path' // 삭제된 파일
   git add 'file path' (or *) // 추가,변경 파일
   git commit -m "commit message" // 커밋
   ```

   <br>

4. **push & pull request**

   - push : 작업 내용을 원격 저장소로 push한다.
     - remote에 해당 branch가 생성되어 있지 않다면, 해당 branch를 생성하여 push한다. <br>(master branch에 직접 push하지 않도록 한다.)

   ```
   git push --set-upstream origin 'branch_name'
   ```

   - pull request : GitHub 에서 Pull Request 작성

     ​	1. Pull Request를 생성한다.

   ![github_create_pr](/files/github_create_pr.png){:width="100%"}

   ​		2. PR Title과 comment(optional)을 입력 후, `Create pull request` 버튼을 클릭한다.

   ![github_open_pr](/files/github_open_pr.png){:width="100%"}

   <br>

5. **review & merge**   `reviewer`

   * review : PR 리뷰 수행 및 개선작업

     1. PR 목록에서 변경사항을 확인한다.

     2. 변경 사항에 inline comment를 작성할 수 있다.

        ![github_add_review_comment](/files/github_add_review_comment.png){:width="100%"}

     3. Review 변경사항을 저장한다.

        ![github_review_change](/files/github_review_change.png){:width="100%"}

        - Comment : 추가적인 comment를 작성할 경우
        - Approve : master branch에 merge할 수 있는 경우
        - Request change : 수정 필요사항이 있을 경우 <br>(`committer`는 해당 요청사항에 따라 코드를 수정하여 3~4과정을 수행한다.)

   * merge : 변경사항을 master branch로 merge한다.

   * Squash and merge를 통해 한 브랜치의 변경 이력을 최신 커밋 하나로 합쳐서 merge할 수 있다.<br>(commit history가 깔끔해 질 수 있음)

     ![github_merge](/files/github_merge.png){:width="100%"}

     * Create a merge commit : 개별 커밋 내역을 적용한 merge commit을 생성하여 merge한다.
     * Squash and merge : 한 브랜치의 변경 이력을 최신 커밋 하나로 합쳐서 merge할 수 있다.<br>(commit history가 깔끔해 질 수 있음)
     * Rebase and merge : rebase 이후 merge한다.


   <br>

6. **checkout master**

   * 변경 사항 적용을 위해 local branch를 master branch로 checkout 한다.

   ```
   git checkout master
   ```

   <br>

7. **pull**

   * 변경 사항 적용을 위해 origin/master branch를 pull한다.

   ```
   git pull
   ```

   

   * 이후 신규 작업은 2~7과정을 통해 진행한다.





<br>참고 : [Youtube - YongWoo Jeon님의 github에서 브랜치를 만들고 PR보내는 방법](https://youtu.be/_giqGNzR1Nc){:target="_blank"}