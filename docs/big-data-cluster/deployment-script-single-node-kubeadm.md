---
title: Развертывание в кластере kubeadm с одним узлом с помощью скрипта bash
titleSuffix: SQL Server big data clusters
description: Используйте скрипт развертывания bash для развертывания [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] в кластере kubeadm с одним узлом.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2379f96e3b5288fc33f5c925613bf9fd5d35612d
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71341838"
---
# <a name="deploy-with-a-bash-script-to-a-single-node-kubeadm-cluster"></a>Развертывание в кластере kubeadm с одним узлом с помощью скрипта bash

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

В этом руководстве вы используете образец скрипта bash для развертывания кластера Kubernetes с одним узлом с помощью kubeadm и последующего развертывания в нем кластера больших данных SQL Server.  

## <a name="prerequisites"></a>предварительные требования

- Виртуальная машина или физический компьютер классического **сервера** Ubuntu 18.04 или 16.04. Все зависимости настраиваются скриптом, который запускается из виртуальной машины.

  > [!NOTE]
  > Использование виртуальных машин Azure Linux пока не поддерживается.

- Виртуальная машина должна иметь по крайней мере 8 ЦП, 64 ГБ ОЗУ и 100 ГБ места на диске. После получения всех образов Docker для кластера больших данных останется 50 ГБ для данных и журналов всех компонентов.

- Обновите существующие пакеты с помощью приведенных ниже команд, чтобы убедиться, что используется актуальный образ ОС.

   ``` bash
   sudo apt update && sudo apt upgrade -y
   sudo systemctl reboot
   ```

## <a name="recommended-virtual-machine-settings"></a>Рекомендуемые параметры виртуальных машин

1. Используйте конфигурацию статической памяти для виртуальной машины. Например, в установках Hyper-V не используйте динамическое выделение памяти, а выделите рекомендуемый объем 64 ГБ или более.

1. Используйте возможность создания контрольных точек или моментальных снимков в гипервизоре, чтобы откатить виртуальную машину до чистого состояния.


## <a name="instructions-to-deploy-sql-server-big-data-cluster"></a>Инструкции по развертыванию кластера больших данных SQL Server

1. Скачайте скрипт в виртуальную машину, которую планируете использовать для развертывания.

   ```bash
   curl --output setup-bdc.sh https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/setup-bdc.sh
   ```

2. Преобразуйте скрипт в исполняемый файл с помощью приведенной ниже команды.

   ```bash
   chmod +x setup-bdc.sh
   ```

3. Запустите скрипт (обязательно используйте *sudo*)

   ```bash
   sudo ./setup-bdc.sh
   ```

   При появлении запроса введите пароль для следующих внешних конечных точек: контроллера, главного экземпляра SQL Server и шлюза. Пароль должен быть достаточно сложным в зависимости от существующих правил для пароля SQL Server. Имя пользователя по умолчанию для контроллера — *admin*.

4. Настройте псевдоним для средства **azdata**.

   ```bash
   source ~/.bashrc
   ```

5. Обновите настройки псевдонима для azdata.

   ```bash
   azdata --version
   ```

## <a name="cleanup"></a>Очистка

Скрипт [cleanup-bdc.sh](https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/cleanup-bdc.sh) предоставляется для удобного сброса среды при необходимости. Однако рекомендуется использовать виртуальную машину для тестирования и использовать возможности создания моментальных снимков в гипервизоре для отката виртуальной машины до чистого состояния.

## <a name="next-steps"></a>Дальнейшие действия

Чтобы приступить к использованию кластера больших данных, см. [Учебник. Загрузка примера данных в кластер больших данных SQL Server](tutorial-load-sample-data.md).
