

### Описание проекта

Здесь я кратко расскажу про каждый этап решения. Названия соответствует секциям в приложеном ноутбуке.

Для достаточно склонировать репозиторий, скопировать сюда intern_task.csv и запустить.

# Data analysis

Для начала нужно было посмотреть, что из себя представляет датасет.  Оказалось, что категориальных признаков не было, а сами признаки были анонимизированы, что усложняет feature engineering (только если пробовать комбинации через AutoML).
Потом я посмотрел на корреляцию признаков между собой и с рангом для поиска закономерностей.

# Data Preprocessing
Обычно я бы начал с нормализации данных, но так как дальше я буду использовать CatBoostRanker, а для градиентного бустинга деревьев не требуется нормализация, то этот этап я пропустил.
Потом разбиение на train/val/test, но такое, которое предотвращает лики групп в разные выборки.

# Model Training
Подбор лучших параметров осуществлялся с помощью оптуны, фокус был на предотвращении оверфита, поэтому я подбирал глубину дерева, l2 регуляризацию листов и random_strength, которые способствуют его снижению. Параметр min_child_leaf не улучшил результат.

Дальше я визуализировал основные показатели метрик.






