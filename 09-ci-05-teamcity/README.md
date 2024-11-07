# Домашнее задание к занятию 11 «Teamcity»

## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.
4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).
6. Создайте VM (2CPU4RAM) и запустите [playbook](./infrastructure).

![1](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/1.png)     


## Основная часть

1. Создайте новый проект в teamcity на основе fork.
2. Сделайте autodetect конфигурации.
3. Сохраните необходимые шаги, запустите первую сборку master.

![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/2.png)         
![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/4.png)       

4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.

![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/5.png)       

5. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.
7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.

![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/6.png)     
![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/7.png)         

8. Мигрируйте `build configuration` в репозиторий.

![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/8-1.png)      
![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/8-2.png)      

9. Создайте отдельную ветку `feature/add_reply` в репозитории.
10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.
11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.
12. Сделайте push всех изменений в новую ветку репозитория.
13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.

![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/9.png)       
![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/10-1.png)     
![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/10-2.png)    
![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/13.png)      

14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.

![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/14.png)     

15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.

![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/15.png)       

16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.

![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/16.png)          

17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.

![](https://github.com/JulieJool/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/img/17.png)         

18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
19. В ответе пришлите ссылку на репозиторий.

[My example-teamcity repository](https://github.com/JulieJool/example-teamcity)      
---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
