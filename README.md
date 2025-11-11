# booker-contracts

Protobuf контракты для системы бронирования столов.

## Описание

Этот репозиторий содержит все `.proto` файлы - единственный источник истины для API контрактов.

## Структура

```
proto-split/
├── booking/      # Контракты для сервиса бронирований
├── venue/        # Контракты для сервиса заведений
└── common/       # Общие типы и события
```

## Генерация Go-кода

Go-код генерируется автоматически в репозиторий `booker-contracts-go` через GitHub Actions.

### Локальная генерация

```bash
# Установить buf (если еще не установлен)
# https://buf.build/docs/installation

# Сгенерировать код
buf generate
```

## Версионирование

- Используется SemVer: `v1.0.0`, `v1.1.0`, `v2.0.0`
- При создании тега автоматически генерируется Go-код в `booker-contracts-go`
- Breaking changes → major version (v2, v3, ...)

## Использование в сервисах

```go
import (
    bookingpb "github.com/bookingcontrol/booker-contracts-go/v1/booking"
    venuepb "github.com/bookingcontrol/booker-contracts-go/v1/venue"
    commonpb "github.com/bookingcontrol/booker-contracts-go/v1/common"
)
```

## Разработка

1. Измени `.proto` файлы
2. Создай PR
3. После merge создай тег: `git tag v1.1.0 && git push origin v1.1.0`
4. GitHub Actions автоматически сгенерирует Go-код
