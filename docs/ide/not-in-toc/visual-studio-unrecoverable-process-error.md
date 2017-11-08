---
title: Nicht behebbare Prozessfehler in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 02/23/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 2263956f-3ae0-4bdc-9d3a-4991dfaf4ddb
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology:
- vs-ide-general
ms.translationtype: Human Translation
ms.sourcegitcommit: b5f39ea962f6b4dcc0e2c6947b2eeabf53d3329a
ms.openlocfilehash: ba0a0aacc68e2eb9a5cd9b5b672808a71e8c09eb
ms.contentlocale: de-de
ms.lasthandoff: 03/01/2017

---
# <a name="visual-studio-unrecoverable-process-error"></a>Nicht behebbare Prozessfehler in Visual Studio

Visual Studio 2017 verwendet mehrere Out-of-Proc-Prozesse, um die erforderlichen Hintergrundaufgaben, wie z.B. Live-Komponententests, Code-Analyzer und mehr auszuführen. Diese Prozesse werden Out-of-Proc ausgeführt, um Leistungsvorteile von Visual Studio zu nutzen, z.B. dass Visual Studio schneller reagieren kann, wenn ressourcenintensive, langfristige Jobs ausgeführt werden. Da Visual Studio ein 32-Bit-Prozess ist, bietet die Out-of-Proc-Ausführung von Prozessen anspruchsvollen speicherintensiven Arbeiten einen größeren Speicherplatz, in dem ausgeführt werden soll.

Wenn einer dieser erforderlichen Prozesse aus irgendeinem Grund endet, wird eine Popup Informationsleiste mit der folgenden Meldung angezeigt:

„Unfortunately, a process used by Visual Studio has encountered an unrecoverable error. We recommend saving your work, and then closing and restarting Visual Studio.“ (Leider ist bei einem Prozess mit Visual Studio ein nicht behebbarer Fehler aufgetreten. Wir empfehlen Ihnen, Ihre Arbeit abzuspeichern und Visual Studio anschließend neu zu starten.)

Wenn diese Meldung angezeigt wird, müssen Sie Ihre Arbeit sofort speichern, und anschließend Visual Studio schließen und neu starten. Wenn Sie dies nicht tun, kann Visual Studio jederzeit abstürzen.

## <a name="list-of-processes"></a>Liste der Prozesse

Es folgt eine Liste der von Visual Studio verwendeten Out-of-Proc-Prozesse, die ausgeführt werden müssen, sodass Visual Studio ordnungsgemäß arbeitet.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe

