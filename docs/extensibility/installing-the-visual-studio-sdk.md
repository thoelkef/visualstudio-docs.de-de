---
title: Installieren des Visual Studio SDK | Microsoft Docs
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f391708abbd8a9b66f2dfd5aaa6559cb075910d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710347"
---
# <a name="install-the-visual-studio-sdk"></a>Installieren des Visual Studio SDK

Das Visual Studio SDK (Software Development Kit) ist eine optionale Funktion in Visual Studio-Setup. Sie können das VS SDK auch später installieren.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installieren des Visual Studio SDK als Teil einer Visual Studio-Installation

Um das VS SDK in Ihre Visual Studio-Installation einzubeziehen, installieren Sie die **Visual Studio-Erweiterungsentwicklungsarbeitsauslastung** unter **Andere Toolsets**. Diese Arbeitsauslastung installiert das Visual Studio SDK und die erforderlichen Voraussetzungen. Sie können die Installation weiter optimieren, indem Sie Komponenten aus der **Zusammenfassungsansicht** auswählen oder deaktivieren.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Installieren des Visual Studio SDK nach der Installation von Visual Studio

Um das Visual Studio SDK nach Abschluss der Visual Studio-Installation zu installieren, führen Sie das Visual Studio-Installationsprogramm erneut aus, und wählen Sie die **Visual Studio-Erweiterungsentwicklungsarbeitsauslastung** aus.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Installieren des Visual Studio SDK aus einer Lösung

Wenn Sie eine Projektmappe mit einem Erweiterbarkeitsprojekt öffnen, ohne das VS SDK vorher zu installieren, werden Sie von einem Dialogfeld **Fehlendes Feature installieren** aufgefordert, die **Visual Studio-Erweiterungsentwicklungsarbeitsauslastung** zu installieren:

![Installieren der Erweiterungsentwicklung](../extensibility/media/install-extension-development.png "Installieren der Erweiterungsentwicklung")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Installieren des Visual Studio SDK über die Befehlszeile

Wie bei jeder Visual Studio-Workload oder -Komponente können Sie auch die **Visual Studio-Erweiterungsentwicklungsarbeitsauslastung** (ID: Microsoft.VisualStudio.Workload.VisualStudio)" über die Befehlszeile installieren. Weitere Informationen zu den entsprechenden Befehlszeilenwechseln und allgemeinen Anweisungen zum Bestimmen von Arbeitsauslastungs- oder Komponentenbezeichnern finden Sie unter Verwenden von [Befehlszeilenparametern zum Installieren](../install/use-command-line-parameters-to-install-visual-studio.md) von Visual Studio.

Beachten Sie, dass Sie das Visual Studio-Installationsprogramm verwenden müssen, das mit der installierten Version von Visual Studio übereinstimmt. Wenn Sie beispielsweise Visual Studio Enterprise auf Ihrem Computer installiert haben, müssen Sie das Visual Studio Enterprise-Installationsprogramm (*vs_enterprise.exe*) ausführen.
