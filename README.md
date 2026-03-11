mkdir git-practice
cd git-practice
git init
echo "Первый файл - начальное содержимое" > pal.txt
echo "Второй файл - начальное содержимое" > pil.txt
echo "Третий файл - начальное содержимое" > pul.txt
git add pal.txt pil.txt
git commit -m "Коммит 2 файлов (pal и pil)"
git add pul.txt
git commit -m "Коммит оставшегося файла pul"
echo "Добавленные данные в первый файл" >> pal.txt
git add pal.txt
git commit -m "Добавлены данные в pal"
git checkout -b feature-branch-1
echo "Полностью измененное содержимое первого файла в ветке feature-branch-1" > pal.txt
git add pal.txt
git commit -m "Полное изменение pal в ветке feature-branch-1"
git checkout main
git merge feature-branch-1
echo "Добавленные данные во второй файл" >> pil.txt
git add pil.txt
git commit -m "Добавлены данные в pil"
git checkout -b feature-branch-2
echo "Полностью измененное содержимое второго файла в ветке feature-branch-2" > pil.txt
git add pil.txt
git commit -m "Полное изменение pil в ветке feature-branch-2"
git checkout main
echo "Полностью измененное содержимое второго файла в основной ветке" > pil.txt
git add pil.txt
git commit -m "Полное изменение pil в основной ветке"
git merge feature-branch-2
echo "Полностью измененное содержимое второго файла в основной ветке" > pil.txt
git add pil.txt
git commit -m "Resolved merge conflict - kept main version"
git remote add origin https://github.com/ВАШ-ЛОГИН/НАЗВАНИЕ-РЕПОЗИТОРИЯ.git
git branch -M main
git push -u origin main
echo "Изменение в третьем файле перед созданием ветки" > pul.txt
git checkout -b feature-branch-3
git add pul.txt
git commit -m "Изменение pul в ветке feature-branch-3"
git push -u origin feature-branch-3
cd ..
git clone https://github.com/ВАШ-ЛОГИН/НАЗВАНИЕ-РЕПОЗИТОРИЯ.git git-practice-clone
cd git-practice-clone
git fetch origin feature-branch-3
git checkout feature-branch-3
git checkout main
git merge feature-branch-3
git push origin main
cd ../git-practice
echo "Изменение во втором файле в оригинальном репозитории" >> pil.txt
git add pil.txt
git commit -m "Изменение pil в оригинальном репозитории"
git push
git fetch origin
git merge origin/main --allow-unrelated-histories
git add pil.txt
git commit -m "Merge remote changes"
git push
git log --oneline --graph --all
git push --all origi
