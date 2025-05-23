Описание проекта
KafedraMeetingApp — это мобильное приложение для Android, разработанное для управления заседаниями кафедры. Приложение позволяет пользователям просматривать, создавать, редактировать и архивировать записи о заседаниях,
а также получать уведомления о предстоящих событиях. Оно интегрировано с Firebase для хранения данных, аутентификации и отправки push-уведомлений. Приложение поддерживает разные роли пользователей: администраторы (например, 
пользователь с email yaniayurieva@gmail.com) имеют расширенные права для создания, редактирования и удаления заседаний, в то время как обычные пользователи могут только просматривать информацию.
Приложение разработано в рамках курсовой работы и демонстрирует использование современных технологий Android, включая Firebase Realtime Database, Firebase Cloud Messaging (FCM), WorkManager и AndroidX.

Структура проекта
com.example.kafedrameetingapp/
├── adapters/
│   └── MeetingAdapter.java        # Адаптер для отображения списка заседаний
├── models/
│   └── Meeting.java              # Модель данных заседания
├── utils/
│   ├── AlarmUtils.java           # Утилиты для планирования уведомлений
│   └── FirebaseUtils.java        # Утилиты для работы с Firebase
├── work/
│   ├── NotificationReceiver.java # Приемник для обработки уведомлений
│   └── NotificationWorker.java   # Фоновая задача для проверки уведомлений
├── MainActivity.java             # Главная активность (список текущих заседаний)
├── CreateMeetingActivity.java    # Активность для создания/редактирования заседаний
├── LoginActivity.java            # Активность для входа/регистрации
├── ArchiveActivity.java          # Активность для просмотра архива
├── MeetingDetailActivity.java    # Активность для просмотра деталей заседания
├── MeetingApp.java               # Класс приложения для инициализации Firebase
└── MyFirebaseMessagingService.java # Сервис для обработки FCM-уведомлений

Настройка Firebase
Создайте проект в Firebase Console.
Добавьте приложение Android в проект Firebase:
Укажите пакет com.example.kafedrameetingapp.
Скачайте файл google-services.json и поместите его в папку app/ проекта.
Включите следующие сервисы в Firebase Console:
Authentication: Включите вход по email/паролю.
Realtime Database: Создайте базу данных и настройте правила доступа.
Cloud Messaging: Настройте FCM для push-уведомлений.
В файле build.gradle (уровень проекта) добавьте:
classpath 'com.google.gms:google-services:4.4.2'
В файле build.gradle (уровень модуля app) добавьте:
apply plugin: 'com.google.gms.google-services'
dependencies {
    implementation 'com.google.firebase:firebase-auth:23.0.0'
    implementation 'com.google.firebase:firebase-database:21.0.0'
    implementation 'com.google.firebase:firebase-messaging:24.0.0'
    implementation 'androidx.work:work-runtime:2.9.1'
    implementation 'androidx.recyclerview:recyclerview:1.3.2'
}


Установка и запуск
Склонируйте репозиторий:
git clone <URL_репозитория>

Откройте проект в Android Studio.


Синхронизируйте проект с Gradle (нажмите «Sync Project with Gradle Files»).


Подключите устройство Android или используйте эмулятор с API 21+.

Нажмите «Run» в Android Studio для сборки и запуска приложения.




Использование
Запуск приложения:
При первом запуске откроется экран входа (LoginActivity).
Регистрация/вход:


Зарегистрируйтесь, указав email и пароль (не менее 6 символов).


Войдите, используя существующие учетные данные.


Работа с заседаниями:



На главном экране (MainActivity) отображается список текущих заседаний.


Нажмите на заседание, чтобы открыть детали (MeetingDetailActivity).


Нажмите «Архив» для просмотра прошедших заседаний (ArchiveActivity).


Если вы администратор (yaniayurieva@gmail.com)(введите пароль 123456), нажмите «Создать заседание» для добавления нового (CreateMeetingActivity).



Уведомления:


Разрешите уведомления при запросе (для Android 13+).


Вы получите уведомления за 60 и 15 минут до заседания.


Выход:



Нажмите «Выйти» на главном экране, чтобы завершить сеанс.
