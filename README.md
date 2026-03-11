mkdir my-git-project
cd my-git-project
git init
echo "Файл 1 - начальное содержание" > file1.txt
echo "Файл 2 - начальное содержание" > file2.txt
echo "Файл 3 - начальное содержание" > file3.txt
git add file1.txt file2.txt
git commit -m "Добавлены файлы 1 и 2"
git add file3.txt
git commit -m "Добавлен файл 3"
echo "Дополнительные данные в файл 1" >> file1.txt
git add file1.txt
git commit -m "Добавлены данные в file1.txt"
git branch feature-branch
git checkout feature-branch
echo "Полностью новые данные в файле 1 в ветке feature-branch" > file1.txt
git add file1.txt
git commit -m "Полное изменение file1.txt в feature-branch"
git checkout main
git merge feature-branch
echo "Данные добавлены в файл 2 в основной ветке" >> file2.txt
git add file2.txt
git commit -m "Добавлены данные в file2.txt в main"
git checkout -b conflict-branch
echo "Полностью измененные данные в файле 2 в конфликтующей ветке" > file2.txt
git add file2.txt
git commit -m "Полное изменение file2.txt в conflict-branch"
git checkout main
echo "Полностью измененные данные в файле 2 в основной ветке" > file2.txt
git add file2.txt
git commit -m "Полное изменение file2.txt в основной ветке"
git merge conflict-branch || true
git checkout --ours file2.txt
git add file2.txt
git commit -m "Слито conflict-branch с разрешением конфликта в пользу основной ветки"
git remote add origin https://github.com/Kilulu1/per/blob/main/README.md?plain=1
git branch -M main
git push -u origin main
git checkout -b new-feature
echo "Изменения в файле 3 в новой ветке" > file3.txt
git add file3.txt
git commit -m "Изменен file3.txt в new-feature"
git push -u origin new-feature
cd ..
git clone https://github.com/Kilulu1/per/blob/main/README.md?plain=1 my-git-project-clone
cd my-git-project-clone
git fetch origin new-feature
git checkout new-feature
git checkout main
git merge new-feature
git push origin main
cd ../my-git-project
echo "Локальные изменения в файле 2" >> file2.txt
git add file2.txt
git commit -m "Локальные изменения file2.txt"
git push || echo "Ожидаемо не удалось отправить изменения"
git pull origin main --rebase
git log --oneline --graph --all --decorate
git status
