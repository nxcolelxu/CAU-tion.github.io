---
title: "Markdown에서 이미지 첨부 using Github Issue"
excerpt: "Markdown에서 이미지를 첨부할 때, 이미지 파일을 추가하는 방식 대신 github issue를 이용하여 이미지의 주소를 삽입하는 방식에 관하여 포스팅하였습니다."
author: 1unaram
categories:
    - etc
tags:
    - [markdown, github]
date: 2025-03-04
last_modified_at: 2025-03-04
---

# Insert image in Markdown

---

마크다운 문법을 사용하여 이미지를 삽입할 때에는 두 가지 방식이 존재합니다.

<br>

1. `![image_title](image_path)`

    위와 같이 이미지 제목과 이미지가 존재하는 경로를 명시해주는 방식입니다. 이 방식은 크기와 같은 스타일 조절이 불가능하다는 단점이 있습니다.

    <br>

    [예시]

    ```markdown
    ![CAUtion_logo_mint](/assets/images/cau-tion-logo-mint.png)

    ![CAUtion_logo_white](https://cau-tion.com/logo_white.png)
    ```

<br>

2. `<img src="image_path">`

    위와 같이 HTML img 태그와 src 속성에 이미지가 존재하는 경로를 명시해주는 방식입니다. 이 방식은 img 태그의 속성을 이용할 수 있어 크기와 같은 스타일 조절이 가능합니다.

    <br>

    [예시]

    ```markdown
    <img src="/assets/cau-tion-logo-mint.png">
    <img src="/assets/cau-tion-logo-mint.png" style="width:100px">
    <img src="/assets/cau-tion-logo-mint.png" style="width:100px;border:1px solid black">
    ```

<br>

**이때, 이미지 파일을 제공하는 서버 URL이 존재하지 않는다면,** <u>1) 이미지 파일이 같은 프로젝트 내에 존재해야 하며 2) 이미지 파일의 경로를 명시해주어야 합니다.</u> 이를 위해 프로젝트 내에 이미지 파일이 존재하기 위한 저장공간이 필요합니다.

따라서 우리는 이미지 파일을 제공하는 기능을 하는 Github 서버에 이미지 파일을 업로드하여 해당 URL을 참조하면 이미지 파일을 저장하지 않더라도 이미지를 사용할 수 있습니다.

<br>
<br>

# Github Issue

Step1. 우선 첨부하고자 하는 이미지를 **복사(Ctrl+C)** 합니다.

<br>
<br>

Step2. 본인 계정의 임의의 Github repository에 들어간 후 상단 탭 중 **_Issues_** 탭에 들어갑니다(사용하지 않는 repository이어도 상관없습니다).

<img src="https://github.com/user-attachments/assets/8cfd831d-ea84-48a2-bed0-495ff03d909f">

<br>
<br>

Step3. 본문에 이미지 파일을 **붙여넣기(Ctrl+V)** 합니다. 잠시 기다리면 아래와 이미지와 같이 markdown 형식으로 이미지가 삽입된 것을 확인할 수 있습니다.

<img src="https://github.com/user-attachments/assets/8d77fd83-8cb5-40bb-8c9e-ded17c3c4bef">

💡 이미지를 Issue 탭에 복사 붙여넣기 하지 않고 드래그 앤 드롭 하여도 작동합니다
{: .notice--info}

<br>
<br>

Step4. `image_path` 자리인 URL을 복사하여 원하는 곳에 사용하면 됩니다. 이는 이미지가 Github 서버에 저장된 것이기에 현재 만든 Issue를 Create 하지 않아도 참조가 가능합니다.

```markdown
![CAUtion_logo_mint](https://github.com/user-attachments/assets/e41b67b1-fa86-4339-961e-c4aeadade276)

<img src="https://github.com/user-attachments/assets/fb421c42-803b-4e80-8e1d-190d87fed90c">
```
