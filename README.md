# README.MD

> forked from : [tech.kakao.com](https://github.com/kakao/kakao.github.io)
>
> base branch fork하여 사용할 것
>
> * master branch는 <http://huansuh.github.io> 
>
> 주의: [GitHub Pages]와 [Jekyll]에 대해서 충분히 숙지할 것.





## How to use

### Post 등록

1. `_posts` 디렉토리에 `yyyy-mm-dd-slug.md` 파일로 복사(or 이동).
 - slug: 해당 포스트의 고유 키로 url의 일부로 사용. 왠만하면 특수문자없이 영문자,숫자,-(하이픈),.(점)...만 사용.

 - yyyy,mm,dd: 발행 년,월,일.

 - 참고: 최종적으로 포스트의 url(permalink)는 {site_url}/yyyy/mm/dd/slug/

   * permalink 설정은 `_config.yml` 항목에서 설정

   * ```yaml
     permalink: /:year/:month/:day/:title/
     ```
2. 파일 상단에 [front matter] 작성
 - layout: post # 레이아웃(필수). `page` 레이아웃을 사용하면 목록에 보이지 않는 글을 쓸 수 있음.
 - title: '제목' # 제목(필수)
 - author: `lastname.firstname` # 필자(필수).
   * 처음 글을 쓰는 필자이라면 **Author 등록**(필수)
 - tags: `[tag1,tag2,tag3,...]` # 태그 목록(선택). 왠만하면 특수문자없이 영소문자,숫자,-(하이픈),.(점)...만 사용.
    - 유력한(?) 태그가 새로 등장했다면 **Tag 등록**(선택)
 - image: http://... # 커버이미지 url(선택)
 - date: `YYYY-MM-DD HH:MM:SS` # 발행일(필수)


### Author 등록

1. `_authors` 디렉토리에 `username.md` 이름으로 필자 정보 파일 추가
2. 파일 상단에 [front matter] 작성
 - layout: author # 레이아웃(필수)
 - name: `username` # 왠만하면 특수문자없이 영소문자,숫자,-(하이픈),.(점)...만 사용.
    - post 작성 시 본 name 항목을 frontmatter의 author에 작성한다.
 - title: ... # 왠만하면 한글이름 사용( 필수)
 - image: http://... # 프로필 이미지(필수)
 - cover: http://... # 작성자 커버 이미지(선택)
 - email : # 이메일 주소(선택)
 - social_id : # 각 social service 별 link 계정 id(선택)
3. 내용은 필요없음

```
---
name: 
title: 		     
image: 		     #optional (or [/files/authors/author_name.jpg])
cover: 		     #optional (or [/files/authors/author_name_cover.jpg])
email: 		     #optional
facebook_id:	 #optional
github_id:     	 #optional
---
```



### Tag 등록

1. `_tags` 디렉토리에 `tag-name.md` 이름으로 필자 정보 파일 추가
2. 파일 상단에 [front matter] 작성

* layout: tag # 레이아웃(필수)
* name: `tag-name` # 왠만하면 특수문자없이 영소문자,숫자,-(하이픈),.(점)...만 사용.
  * post 작성 시 본 name 항목을 frontmatter의 tags에 작성한다.
* title: ... # 좀 더 길고 구체적인 설명(필수)
* image: http://... # 태그 이미지(선택)

3. 내용은 필요없음

```
---
name: hello
title: 'Hello Jekyll!!'
image: #optional (or [/files/covers/tag_name.jpg])
---
```







---



## Settings

### Header

![readme_header_mo](/files/readme/readme_header.png)

![readme_header_mo](/files/readme/readme_header_mo.png)



* #### Logo 변경

  1. 아래 파일 resource 변경

     `/assets/images/pc/blog_logo.png`

     `/assets/images/mo/blog_logo.png`

     `/assets/images/mo/blog_logo@2x.png`

     `/assets/images/mo/blog_logo@3x.png`

  2. css 파일 내 사이즈 설정

     `/assets/css/screen.css` 파일 내 `#logo `의 `width`, `height`, `background-size` 항목 설정 변경

     

* #### Favicon 변경

  1. 아래 파일 resource 변경

     `/assets/images/favicon.ico`

     

* #### Menu 등록

  1. `_config.yml`의 `menu_list` 항목에 `menu` 추가

     ```yaml
     menu_list:    # Add menu
       - menu:
         title: About
         permalink: about
       - menu:
         title: 
         permalink: 
     ```

     * `_include/header.html` 내 아래 코드에서 자동으로 메뉴 생성(default 메뉴-Blog 변경 가능)

     ```html
     <ul id="menu" class="nav">
         <li><a href="{{ base_path }}/">Blog</a></li>
         {% for menu in site.menu_list %}
             {% if menu.title and menu.permalink %}
                 {% assign template = '/' | append: menu.permalink | append: '/' %}
                     <li class="{% if page.url == template %} active {% endif %}">
                       <a href="{{ base_path }}/{{menu.permalink}}/">{{menu.title}}</a>
                     </li>
             {% endif %}
         {% endfor %}
     </ul>
     ```



### Footer

* #### Footer menu 등록

  

* #### Social services

  [`_config.yml`](./_config.yml) 에서 개별 social service의 username 항목에 link되는 계정 id 입력 시 footer에 해당 링크 icon 추가됨

  ```yaml
  facebook:
    app_id:
    username:
    comment_enabled: true
  github:
    username:
  ```

  - 현재 facebook, GitHub 등록 가능, 추후 다른 social service 추가 예정



#### Facebook comment

[`_config.yml`](./_config.yml)  에서 facebook.comment_enabled 항목 `true`로 설정

```yaml
facebook:
  app_id:
  username:
  comment_enabled: true
```

![readme_fbcomment](/files/readme/readme_fbcomment.png)









## License

This software is licensed under the [Apache 2 license](LICENSE.txt), quoted below. 

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this project except in compliance with the License. You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0. Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.