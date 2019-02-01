---
title: Bearbeiten und Fortfahren nicht unterstützt für F# | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5b0809b1d6a19a2bb46fefbf90338589de614a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976367"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Bearbeiten und Fortfahren wird für F# nicht unterstützt #
Beim Debuggen von F#-Code wird Bearbeiten und Fortfahren nicht unterstützt. Das Bearbeiten von F#-Code während einer Debugsitzung ist möglich, sollte aber vermieden werden. Codeänderungen werden während der Debugsitzung nicht übernommen. Daher führen alle während des Debuggens an F#-Code vorgenommenen Bearbeitungen dazu, dass der Quellcode nicht mit dem gerade gedebuggten Code übereinstimmt.
