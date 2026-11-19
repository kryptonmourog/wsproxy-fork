# wsproxy-fork

**Русский** | [English](README.md)

Форк [mautrix-wsproxy](https://github.com/mautrix/wsproxy) — прокси, который передаёт мосту транзакции сервера
Matrix по websocket, чтобы мост мог работать на другом сервере без открытых портов.

## Зачем он создан

[telegram-bridge-advanced](https://github.com/kryptonmourog/telegram-bridge-advanced) часто работает на отдельном сервере: в некоторых странах
Telegram с сервера Matrix недоступен. Upstream wsproxy отбрасывает to-device события и счётчики одноразовых и
запасных ключей из транзакций (MSC2409, MSC3202), а без них не работает шифрование между мостом и сервером. Этот
форк их передаёт. Без шифрования он работает так же, как upstream.

## Как использовать

- С matrix-docker-ansible-deploy: [telegram-bridge-advanced-ansible](https://github.com/kryptonmourog/telegram-bridge-advanced-ansible)
  ставит его на сервер Matrix по умолчанию.
- Вручную: образ `ghcr.io/kryptonmourog/wsproxy-fork:<версия>`, настройка как у upstream (`example-config.yaml`,
  [README upstream](https://github.com/mautrix/wsproxy#readme)); для шифрования на сервере Matrix должны быть
  включены MSC2409 и MSC3202.

## Проект

| Репозиторий | Что это |
|---|---|
| [telegram-bridge-advanced](https://github.com/kryptonmourog/telegram-bridge-advanced) | мост: код, образы, инструкция по установке, выпуски |
| [mautrix-go-fork](https://github.com/kryptonmourog/mautrix-go-fork) | форк mautrix-go, с которым собирается мост |
| **wsproxy-fork** (вы здесь) | websocket-прокси для моста на отдельном сервере, с шифрованием |
| [telegram-bridge-advanced-ansible](https://github.com/kryptonmourog/telegram-bridge-advanced-ansible) | установка через matrix-docker-ansible-deploy, в том числе на отдельный сервер |

## Лицензия

AGPL-3.0, как у mautrix-wsproxy.
