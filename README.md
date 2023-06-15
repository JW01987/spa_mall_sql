# Api 명세

|       기능       | Method | URL                                                         | Req                                                                                                                                                         | Res                                                                                                                                                                                                                                                                                                                                                |
| :--------------: | :----: | ----------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 전체 게시글 조회 |  GET   | /api/postlist                                               | -                                                                                                                                                           | 성공 - http status code 200<br>{<br> "success": true,<br> posts<br> } <br><br> 실패 - http status code 404<br> {<br>"msg" : "데이터를 불러올 수 없습니다." <br>}                                                                                                                                                                                   |
|   게시글 조회    |  GET   | /api/posts/search?searchWord=<검색기준>&searchData=<검색어> | Query string - searchType, searchData                                                                                                                       | 성공 - http status code 200<br>{<br> "postId" : 게시글 아이디, <br> "title" : 제목,<br> "writer" : 작성자이름, <br>"date" : 작성 날짜, <br>"content" : 작성내용 <br> } <br><br> 실패 - http status code 404<br> {<br>"msg" : "데이터를 불러올 수 없습니다." <br>}                                                                                  |
|   게시글 작성    |  POST  | /api/post                                                   | {<br>"postId":게시글 아이디,<br> "title" : 제목,<br> "writer" : 작성자이름, <br>"date" : 작성 날짜, <br>"content" : 작성내용 <br> "password":비밀번호 <br>} | 성공 - http status code 200<br>{<br> "success": true,<br>"msg": "저장되었습니다",<br>"createPost":<br>{<br>"postId": 게시글 아이디,<br> "title" : 제목,<br> "writer" : 작성자이름, <br>"date" : 작성 날짜, <br>"content" : 작성내용 <br> "password":비밀번호 <br>} <br> 실패 - http status code 404<br> {<br>"msg" : "저장에 실패했습니다." <br>}  |
|   게시글 수정    |  PUT   | /api/post/update                                            | {<br>"postId":게시글 아이디,<br> "title" : 제목,<br> "writer" : 작성자이름, <br>"date" : 작성 날짜, <br>"content" : 작성내용 <br> "password":비밀번호 <br>} | 성공 - http status code 200<br>{<br>"msg" : "게시글 수정 완료!"<br> } <br><br> 실패 - http status code 404<br> {<br>"msg" : "수정 실패했습니다." <br>}                                                                                                                                                                                             |
|   게시글 삭제    | DELETE | /api/post/delete/:postId/:password                          | path param - password, postId                                                                                                                               | 성공 - http status code 200<br>{<br>"msg" : "게시글 삭제 완료!"<br> } <br><br> 실패 - http status code 404<br> {<br>"msg" : "삭제 실패했습니다." <br>}                                                                                                                                                                                             |
|    댓글 조회     |  GET   | /api/comments/:postId                                       | path param - postId                                                                                                                                         | 성공 - http status code 200<br>{<br>"postId : 게시글 아이디, <br>"content" : 작성내용, <br>"commentId":댓글 아이디<br> } <br><br> 실패 - http status code 404<br> {<br>"msg" : "데이터를 불러올 수 없습니다." <br>}                                                                                                                                |
|    댓글 작성     |  POST  | /api/comment                                                | {<br>"postId : 게시글 아이디, <br>"content" : 작성내용, <br>"commentId":댓글 아이디<br> }                                                                   | 성공 - http status code 200<br>{<br> success: true,<br> msg: "댓글이 등록되었습니다."<br> } <br><br> 실패 - http status code 404<br> {<br> success: false,<br> msg: "해당 댓글아이디는 이미 존재합니다" <br>},<br>{<br>"msg" : "댓글 내용을 입력해주세요." <br>}, <br> {<br> success: false,<br> msg: "해당 게시글이 존재하지 않습니다"<br> } <br> |
|    댓글 수정     |  PUT   | /api/comment/:commentId                                     | path param - commentId                                                                                                                                      | 성공 - http status code 200<br>{<br>"msg" : "댓글 수정 완료!"<br> } <br><br> 실패 - http status code 404<br> {<br>"msg" : "수정 실패했습니다." <br>},<br> {<br>"msg" : "댓글 내용을 입력해주세요." <br>}                                                                                                                                           |
|    댓글 삭제     | DELETE | /api/comment/delete/:commentId                              | path param - commentId                                                                                                                                      | 성공 - http status code 200<br>{<br>"msg" : "댓글 삭제 완료!"<br> } <br><br> 실패 - http status code 404<br> {<br>"msg" : "삭제 실패했습니다." <br>}                                                                                                                                                                                               |
