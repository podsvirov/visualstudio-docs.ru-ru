---
title: 'CA2003: не рассматривайте волокна как потоки | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a8172490b267949686dd3390c85ed6d86531b192
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521178"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003. Не рассматривайте волокна в качестве потоков
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Категория|Microsoft. надежность|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Управляемый поток обрабатывается как поток Win32.

## <a name="rule-description"></a>Описание правила
 Не следует считать, что управляемый поток является потоком Win32. Это волокно. Среда CLR будет выполнять управляемые потоки как волокна в контексте реальных потоков, принадлежащих SQL. Эти потоки могут совместно использоваться несколькими доменами приложений и даже базами данных в SQL Serverном процессе. Использование локального хранилища управляемого потока будет работать, но нельзя использовать локальное хранилище неуправляемого потока или предположить, что код будет снова запущен в текущем потоке ОС. Не изменяйте такие параметры, как языковой стандарт потока. Не вызывайте Креатекритикалсектион или CreateMutex через P/Invoke, так как они нуждаются в том, что поток, который входит в блокировку, должен также выйти из блокировки. Так как это не будет использоваться при использовании волокон, критические разделы и мьютексы Win32 будут бесполезными в SQL. Большую часть состояния можно безопасно использовать в управляемом объекте System. Thread. Сюда входит локальное хранилище управляемого потока и текущий язык и региональные параметры пользовательского интерфейса потока. Однако в целях модели программирования изменить текущий язык и региональные параметры потока при использовании SQL будет невозможно. Это будет реализовано с помощью нового разрешения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Изучите использование потоков и измените код соответствующим образом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует отключать это правило.
