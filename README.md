# My-second-program
我的第二个练习项目
import os
import shutil
import tempfile

def clean_temp_folder():
    temp_dir = tempfile.gettempdir()
    print(f"正在清理临时文件夹: {temp_dir}\n")

    deleted_files = 0
    deleted_dirs = 0

    for item in os.listdir(temp_dir):
        item_path = os.path.join(temp_dir, item)
        try:
            if os.path.isfile(item_path) or os.path.islink(item_path):
                os.remove(item_path)
                deleted_files += 1
            elif os.path.isdir(item_path):
                shutil.rmtree(item_path)
                deleted_dirs += 1
        except Exception as e:
            # 忽略无法删除的文件（一般是正在使用的）
            continue

    print(f"✅ 清理完成！共删除 {deleted_files} 个文件，{deleted_dirs} 个文件夹。")

if __name__ == "__main__":
    clean_temp_folder()
