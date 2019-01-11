---
title: Installieren von Visual Studio SDK | Microsoft-Dokumentation
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33ab695ca8165de97d1be9813ea9ab11449a1527
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836269"
---
# <a name="install-the-visual-studio-sdk"></a>Installieren des Visual Studio SDK

Das Visual Studio-SDK (Software Development Kit) ist eine optionale Funktion in Visual Studio-Setup. Sie können das VS-SDK auch später installieren.  
  
## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installieren Sie Visual Studio SDK als Teil einer Installation von Visual Studio

Installieren Sie das VS-SDK in Visual Studio-Installation enthält, die **Visual Studio-extensionentwicklung** Workload unter **andere Toolsets**. Diese Workload installiert die Visual Studio-SDK und die erforderlichen Voraussetzungen. Sie können die Installation weiter anpassen, durch das Aktivieren oder Deaktivieren von Komponenten aus der **Zusammenfassung** anzeigen.
  
## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Installieren von Visual Studio SDK nach der Installation von Visual Studio

Um nach Abschluss der Installation von Visual Studio zu Visual Studio SDK installieren, führen Sie Visual Studio-Installer erneut aus, und wählen Sie die **Visual Studio-extensionentwicklung** arbeitsauslastung.  
  
## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Installieren von Visual Studio SDK aus einer Projektmappe

Wenn Sie eine Lösung mit ein Erweiterbarkeitsprojekt öffnen, ohne die erste Installation von Visual Studio SDK, werden Sie aufgefordert durch eine **installieren Sie die fehlende Funktion** Dialogfeld zum Installieren der **Visual Studio-extensionentwicklung** Workload:

![Installieren der erweiterungsentwicklung](../extensibility/media/install-extension-development.png "extensionenentwicklung installieren")  
  
## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Installieren von Visual Studio SDK über die Befehlszeile

Mit Visual Studio-arbeitsauslastung oder Komponente, installieren Sie auch können die **Visual Studio-extensionentwicklung** Workload (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) über die Befehlszeile. Finden Sie unter [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) für Informationen zu den entsprechenden Befehlszeilenoptionen und allgemeine Anweisungen zum Ermitteln der arbeitsauslastung oder Komponenten-IDs.
  
Beachten Sie, dass Sie Visual Studio-Installer verwenden müssen, der die installierte Version von Visual Studio entspricht. Z. B. Wenn Sie Visual Studio Enterprise auf Ihrem Computer installiert haben, müssen Sie Ausführen den Installer für Visual Studio Enterprise (*vs_enterprise.exe*).