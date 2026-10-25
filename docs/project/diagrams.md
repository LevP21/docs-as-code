# Диаграммы

## Диаграмма последовательности

```mermaid
sequenceDiagram
    actor User as Специалист по подбору персонала
    participant System as Система анализа резюме
    participant Parser as Модуль извлечения текста
    participant Model as ML-модель

    User->>System: Загрузить резюме
    System->>System: Проверить формат файла
    System->>Parser: Передать файл резюме
    Parser->>Parser: Извлечь текст
    Parser-->>System: Вернуть текст резюме
    System->>Model: Передать текст для анализа
    Model->>Model: Определить навыки, образование и опыт
    Model-->>System: Вернуть результаты анализа
    System-->>User: Показать результаты анализа
```

---

## Диаграмма классов

```mermaid
classDiagram
    class User {
        +int id
        +string name
        +uploadResume()
        +viewResults()
    }

    class Resume {
        +int id
        +string fileName
        +string text
        +uploadDate
    }

    class MLModel {
        +string modelName
        +extractSkills()
        +extractEducation()
        +extractExperience()
    }

    class AnalysisResult {
        +int id
        +string skills
        +string education
        +string experience
    }

    User "1" --> "*" Resume : загружает
    Resume "1" --> "1" MLModel : передаётся на анализ
    MLModel "1" --> "*" AnalysisResult : формирует
    Resume "1" --> "0..1" AnalysisResult : имеет результат
```

---
