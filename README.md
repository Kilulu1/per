mkdir git-practice
cd git-practice
git init
echo "Первый файл - начальное содержимое" > file1.txt
echo "Второй файл - начальное содержимое" > file2.txt
echo "Третий файл - начальное содержимое" > file3.txt
git add file1.txt file2.txt
git commit -m "Коммит 2 файлов (file1 и file2)"
git add pul.txt
git commit -m "Коммит оставшегося файла file3"
echo "Добавленные данные в первый файл" >> file1.txt
git add file1.txt
git commit -m "Добавлены данные в file1"
git checkout -b feature-branch-1
echo "Полностью измененное содержимое первого файла в ветке feature-branch-1" > file1.txt
git add file1.txt
git commit -m "Полное изменение file1 в ветке feature-branch-1"
git checkout main
git merge feature-branch-1
echo "Добавленные данные во второй файл" >> file2.txt
git add file2.txt
git commit -m "Добавлены данные в file2"
git checkout -b feature-branch-2
echo "Полностью измененное содержимое второго файла в ветке feature-branch-2" > file2.txt
git add file2.txt
git commit -m "Полное изменение file2 в ветке feature-branch-2"
git checkout main
echo "Полностью измененное содержимое второго файла в основной ветке" > file2.txt
git add file2.txt
git commit -m "Полное изменение file2 в основной ветке"
git merge feature-branch-2
echo "Полностью измененное содержимое второго файла в основной ветке" > file2.txt
git add file2.txt
git commit -m "Resolved merge conflict - kept main version"
git remote add origin https://github.com/Kilulu1/per.git
git branch -M main
git push -u origin main
echo "Изменение в третьем файле перед созданием ветки" > file3.txt
git checkout -b feature-branch-3
git add file3.txt
git commit -m "Изменение pul в ветке feature-branch-3"
git push -u origin feature-branch-3
cd ..
git clone https://github.com/Kilulu1/per.git git-practice-clone
cd git-practice-clone
git fetch origin feature-branch-3
git checkout feature-branch-3
git checkout main
git merge feature-branch-3
git push origin main
cd ../git-practice
echo "Изменение во втором файле в оригинальном репозитории" >> file3.txt
git add file3.txt
git commit -m "Изменение file3 в оригинальном репозитории"
git push
git fetch origin
git merge origin/main --allow-unrelated-histories
git add file3.txt
git commit -m "Merge remote changes"
git push
git log --oneline --graph --all
git push --all origin
