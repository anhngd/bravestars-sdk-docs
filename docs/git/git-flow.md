---
id: git-flow
title: Quy tắc làm việc trên kho mã nguồn
sidebar_label: Git flow
custom_edit_url: https://git.bravestars.com/system/docs/-/edit/master/docs/git/git-flow.md
---

## Mục đích

Tài liệu này nhằm tạo ra các quy tắc làm việc trên kho mã nguồn trong quá trình cộng tác giữa các thành viên trong Team


## Trước khi làm việc
* Central Repository đã được tạo trên Gitlab.
* Branch mặc định của Central Repository là master.
* Các thành viên có thể fork đối với Central Repository.

## Thuật ngữ
|Thuật ngữ| Ý nghĩa |
|---|---|
|Central Repository | Kho code chính của dự án |
|Forked Repository | Được fork từ kho code chính, là kho code làm việc chính của mỗi thành viên|

## Một số quy tắc

* Không hạn chế số lượng commit với mỗi một pull-request.
* Mỗi Pull-request tương ứng với một issue/task.
* Tiêu đề của Pull-request phải đặt tương ứng với **title** của task với format `refs [Loại issue] #[Số issue] [Nội dung issue]` （Ví dụ: `refs bug #8888 Sửa lỗi 111222`）.
* Đối với commit, trong trường hợp pull-request đó chỉ có 1 commit thì có thể đặt tiêu đề commit tương tự như trên là `refs [Loại issue] #[Số issue] [Nội dung issue]` （Ví dụ: `refs bug #8888 Sửa lỗi 111222`）.\
  Tuy nhiên với trường hợp 1 pull-request có chứa nhiều commit thì cần phải ghi rõ trong nội dung Tiêu đề commit là trong commit đó xử lý đối ứng vấn đề gì.
    * Ví dụ:
        1. Tiêu đề Pull-request: `refs bug #8888 Sửa lỗi cache`
        2. Trong trường hợp pull-request có 2 commit thì nội dung tiêu đề commit của 2 commit sẽ tương ứng như sau
            * `Tạo method thực hiện việc clear cache trong Model`
            * `Tại controller gọi method ở Model để thực hiện việc clear cache`
* Tại Local Repository (trên máy làm việc của Developer): Mỗi developer phải thao tác trên Branch riêng để thực hiện task. **Tuyệt đối không được thay đổi** code khi ở nhánh master.

## Bắt đầu làm việc

0. Cấu hình thông tin của git tại môi trường làm việc cá nhân

```sh
git config --global user.name "Anh Nguyen"
git config --global user.email anhnd@bravestars.com
```

1. Trên [https://git.bravestars.com](https://git.bravestars.com), fork Central Repository về tài khoản của cá nhân (được gọi là Forked Repository）.

2. Clone (tạo bản sao) Forked Repository lên môi trường local. Tại thời điểm này, Forked Repository sẽ được tự động đăng ký dưới tên là `origin`.
    ```sh
    $ git clone [URL của Forked Repository]
    ```

3. Truy cập vào thư mục đã được tạo ra sau khi clone, đăng ký Central Repository dưới tên `upstream`.
    ```sh
    $ cd [thư mục được tạo ra]
    $ git remote add upstream [URL của Central Repository]
    ```

## Các thao tác xử lý trên kho mã nguồn

**Chú ý:** Central Repository và Forked Repository sẽ được gọi tương ứng là `upstream` và `origin`.

1. Đồng bộ hóa branch master tại local với upstream.
    ```sh
    $ git checkout master
    $ git pull upstream master
    ```

2. Tạo branch để làm task từ branch master ở local. Tên branch là số issue của task（Ví dụ: `task/1234`）.
    ```sh
    $ git checkout master
    $ git checkout -b task/1234
    ```

3. Tiến hành làm task（Có thể commit bao nhiêu tùy ý）.

4. Push code lên origin.

    ```sh
    $ git push origin task/1234
    ```

5. Tại origin trên Gitlab、từ branch `task/1234` đã được push lên hãy gửi pull-request đối với branch `master` của `upstream`.
   
6. Quay trở lại 1.

### Xử lý conflict xảy ra trong quá trình rebase

Khi xảy ra conflict trong quá trình rebase, sẽ có hiển thị như dưới đây (tại thời điểm này sẽ bị tự động chuyển về một branch vô danh)
```sh
$ git rebase master
First, rewinding head to replay your work on top of it...
Applying: refs #1234 Sửa lỗi cache
Using index info to reconstruct a base tree...
Falling back to patching base and 3-way merge...
Auto-merging path/to/conflicting/file
CONFLICT (add/add): Merge conflict in path/to/conflicting/file
Failed to merge in the changes.
Patch failed at 0001 refs #1234 Sửa lỗi cache
The copy of the patch that failed is found in:
    /path/to/working/dir/.git/rebase-apply/patch

When you have resolved this problem, run "git rebase --continue".
If you prefer to skip this patch, run "git rebase --skip" instead.
To check out the original branch and stop rebasing, run "git rebase --abort".
```

1. Hãy thực hiện fix lỗi conflict thủ công（những phần được bao bởi <<< và >>> ）.
Trong trường hợp muốn dừng việc rebase lại, hãy dùng lệnh `git rebase --abort`.

2. Khi đã giải quyết được tất cả các conflict, tiếp tục thực hiện việc rebase bằng:

    ```sh
    $ git add .
    $ git rebase --continue
    ```

### Một số câu lệnh git hay dùng

#### Xóa một nhánh

```
git branch -d [Tên branch]
```