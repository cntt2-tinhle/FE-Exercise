Nơi lưu trữ program và file ở trong hệ thống quản lý Version

Trên Git chia repository thành 2 loại là Local repository và Remote repository

Local repository

Repository đang thao tác hiện tại, trong trường hợp thao tác chủ yếu trên máy tính cá nhân hoặc server phát triển gọi là local repository

Ngoài ra, có thể sao chép repository từ remote repository và xây dựng môi trường trên máy tính cá nhân hoặc server

Remote repository

Repository nằm ngoài, có thể thao tác thông qua local repository

Có thể sử dụngg trong trường hợp nhiều người thao tác , public trên internet

Working tree

Nơi user edit, tạo file mới

Index

Nơi bảo trì trạng thái sau khi edit trên working tree là đối tượng tiếp theo trước khi commit lên repository

Branch

Dùng để phân nhánh và ghi chép lịch sử. Nhánh đã chia không bị ảnh hưởng của nhánh khác nên có thể cùng có nhiều thay đổi trong repository giống nhau

Trên Git có 3 loại local branch, remote branch, remote tracking branch

Local branch: Branch có thể quản lý trong local repository

Remote branch: Branch ở trong remote repository

Remote tracking branch: Branch để local repository tracking (theo dõi) remote branch. Ví dụ origin/master biểu thị cho việc đang tracking branch master có ở remote repository gọi là origin

Check out

Triển khai branch ở repository lên working tree

Trên Git không chỉ branch mà tag, Specific commit, branch của remote repository cũng có thể check out

Tag

Tên được gắn vào để có thể dễ dàng tham chiếu commit

Commit

Message gắn vào khi thay đổi file

Revision

Hash value được tạo mỗi lần commit

Trên Git sử dụng hash value và thực hiện quản lý theo thế hệ

HEAD

Từ chỉ định commit mới nhất của branch đang check out hiện tại

FETCH_HEAD

Từ chỉ định commit mới nhất của remote branch đã lấy cuối cùng

ORIG_HEAD

Từ chỉ giá trị HEAD trước đó

MERGE_HEAD

Được tạo ra trong quá trình trộn, ghi lại commit trộn branch

Workflow cơ bản

Tạo repository Tạo file và edit (working tree) Ghi chép lên index Commit lên repository

Thiết lập ban đầu

Tạo repository

#tạo repository

git init

ls a

.   ..   .git

#folder và file được tạo

cd .git

ls

HEAD       description info       refs

config     hooks       objects
Tạo địa chỉ và tên sử dụng trên Git

#thiết lập global

git config --global user.name "username"

git config --global user.email "email"


#repository

git config user.name "username"

git config user.email "email"
Command cơ bản

Ghi file lên index

git add filename

#chỉ định current directory

git add .

#ghi tất cả file

git add --all
Commit thay đổi lên local repository

Commit thay đổi của file đã ghi lên index vào repository

#commit

git commit -m 'message'

#ghi từ working tree lên index và commit

git commit -am 'message'

#thay đổi message commit

git commit --amend
Out put sự khác biệt

Xác nhận sự khác biệt của index với working tree

git diff

#sự khác biệt của file chỉ định

git diff filename

#sự khác biệt giữa branch và commit

git diff branch 1 branch 2

#sự khác biệt giữa branch checkout và index

git diff --cached
Hiển thị Commit log

#out put Commit log

git log

#tóm lược và out put commit log

git shortlog

#out put commit log trên 1 dòng

git log --oneline
Xác nhận trạng thái Local repository và working tree

git status

Hiển thị liên quan đến commit

On branch master * Commit ở trạng thái này sẽ được commit vào branch master
Nothing to commit * Không có thay đổi đối với working tree và index
Changes to be committed * File đang hiển thị là đối tượng commit tiếp theo
Changed but not updated * Đang được thay đổi trên working tree nhưng thay đổi đó không được ghi trên index
Untracked files * Tồn tại trên working tree nhưng không phải đối tượng quản lý của git
Hiển thị liên quan đến trạng thái của file

New file * File đã được hiển thị mới trên index
Modified * Biểu thị việc đã được thay đổi trạng thái từ working tree và index
Renamed * Hiển thị trong trường hợp di chuyển file, thay đổi tên file
Deleted * Được hiển thị trong trường hợp xóa file
Both modified * Hiển thị đối với file trong trường hợp bị mất khi merge và rebase, thay đổi được thêm vào nhiều branch
Unmerged * Hiển thị khi nằm ngoài both modified ra trong trường hợp bị mất khi merge và rebase
Di chuyển, thay đổi/xóa file

#di chuyển, thay đổi

git mv

#xóa

git rm
Local repository, index quay trở lại trạng thái ban đầu

#quay lại trạng thái index, working tree,tham chiếu của HEAD

git reset --hard

#chỉ thay đổi tham chiếu của HEAD

git reset --soft

#thay đổi tham chiếu của HEAD và index. Default git reset

git reset -mixed
Làm sạch working free

#xóa file không được quản lý trên repository

git clean -f


#xác nhận file được xóa

git clean -n

#xóa Directory

git clean -d
Tìm kiếm string đặc định

git grep XXX

Hiển thị nội dung commit

git show

Trường hợp dùng remote repository

Tạo bản sao remote repository

git clone remote repository

Ghi/ thay đổi/ xóa remote repository

#ghi

git remote add tên repository path

#thay đổi

git remote update

#thay đổi repository đặc định

git remote update tên repository

#xóa

git remote rm tên repository

#xóa branch không tồn tại

git remote prune
Reflection dữ liệu remote repository lên local repository

#chỉ định, Reflection remote repository và branch

git pull origin remote branch
Về command git pull

Command git pull là sự kết hợp giữa command　git fetch và git merge

Lấy dữ liệu của repository từ remote repository

#chỉ định branch ở trạng thái repository đã ghi
 

git fetch origin remote repository
Dữ liệu đã lấy được check out như FETCH_HEAD

Sự khác nhau giữa fetch và remote update

Fetch * Lấy thay đổi ở Branch unit
Remote update * Lấy thay đổi ở repository unit
Trộn branch

#chỉ định và trộn branch

git merge tên branch

#chỉ định và trộn commit message

git merge tên branch -m 'message'

Gửi dữ liệu của local repository đến remote repository

#gửi branch「master」đến remote repository「origin」

git push origin tên local branch

#chỉ định branch của nơi Reflection

git push origin tên local branch: tên remote branch
Trường hợp git push lỗi

Trường hợp có commit chỉ ở repository
Trường hợp remote branch đang được check out
Tạo, xác nhận, thay đổi, xóa branch

#tạo trên local repository

git branch tên branch

#xác nhận local branch

git branch

#xác nhận Remote tracking branch

git branch -r

#xác nhận commit mới nhất của mỗi branch

git branch -v

#thay đổi tên branch

git branch -m tên branch (old) tên branch (new)

#xóa branch

git branch -d tên branch

#xóa remote branch (sau khi đã xóa local branch)

git push origin : tên branch
Check out của branch

git checkout tên branch

Có sự thay đổi trên working free và index,check out thì sự thay đổi cứ giữ như thế được Reflection lên branch khác

Tuy nhiên trong sẽ bị lỗi trong trường hợp có sự thay đổi ở file giống nhau trên branch của nơi check out

Gắn tag

#danh sách tag

git tag

#gắn tag

git tag tên tag Revision

#gắn message vào tag

git tag -m ‘message’


#Reflection lên remote

git push origin tên tag

#xóa tag

git tag -d tên tag

#hiển thị tag gần đây nhất

git describe
Compliance commit của branch đang check out trên branch đã chỉ định

git rebase tên branch

Trong trường hợp check out từ branch master sang branch test và đã edit, ghi, commit và rebase thì commit của branch test trên HEAD của branch master sẽ compliance

Sự khác nhau giữa merge và rebase

Merge * Không thay đổi commit trên branch đang check out mà merge các branch
Rebase * Compliance commit của branch đang check out ở commit mới nhất của branch đã chỉ định
Tóm lại merge và rebase khác nhau ở commit
Command thuận tiện

Tạo snap shot của commit chỉ định

git archive --format= Format name --prefix= tên file sau khi triển khai tên commit > tên file

Lưu đồng thời trạng thái commit

#lưu

git stash

#gắn message và lưu

git stash save message

#hiển thị list đã lưu

git stash list

#quay lại nội dung đã lưu

git stash pop

#xóa tất cả nội dung đã lưu

git stash clear
Kiểm tra commit không bao gồm trong branch

git cherry -v nguồn điều tra nơi điều tra

Lấy commit đặc định vào branch

git cherry-pick commit muốn lấy
Chỉ định vị trí bug nhập vào

git bisect start

git bisect good

git bisect bad

#chạy tự động

git bisect run
Làm sạch object của repository

git gc

Hiển thị chuỗi thời gian của lịch sử commit

git reflog

Refspec là gì?

Refspec là link branch giữa local repository với remote repository

git push origin refs/hands/remote branch (nguồn tham chiếu):refs/hands/local branch(nơi tham chiếu)

Ngoài ra cũng có thể chỉ định config