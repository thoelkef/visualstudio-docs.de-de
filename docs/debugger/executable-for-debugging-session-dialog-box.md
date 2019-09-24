---
title: Ausführbare Datei für Debugsitzung (Dialog Feld) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14d4ac95aae860e0750af66aec6adb2969434f11
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211049"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Ausführbare Datei für die Debugsitzung (Dialogfeld)

Dieses Dialogfeld wird angezeigt, wenn Sie eine DLL debuggen, für die keine ausführbare Datei festgelegt wurde. Visual Studio kann eine DLL nicht direkt starten. Stattdessen wird die angegebene ausführbare Datei von Visual Studio gestartet. Sie können die DLL Debuggen, wenn Sie von der ausführbaren Datei aufgerufen wird.

 **Name der ausführbaren Datei** Geben Sie den Pfadnamen in eine ausführbare Datei ein, die die zu debuggende DLL aufruft.

 **URL, an die auf das Projekt zugegriffen werden kann (nur ATL-Server)** Wenn Sie eine ATL-Server-DLL Debuggen, geben Sie die URL ein, unter der sich das Projekt befindet.

 Nachdem Sie diese Einstellungen eingegeben haben, werden Sie auf den Eigenschaften Seiten des Projekts gespeichert, sodass Sie Sie nicht erneut für nachfolgende Debugsitzungen eingeben müssen. Wenn Sie diese Einstellungen ändern möchten, können Sie die Eigenschaftenseiten öffnen und die Werte ändern. Weitere Informationen zum Angeben einer ausführbaren Datei für die Debugsitzung finden Sie unter [Debuggen von DLLs](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)