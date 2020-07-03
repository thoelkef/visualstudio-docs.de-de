---
title: Installieren von Visual Studio SDK | Microsoft-Dokumentation
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31df92b011336320d759461ed16ce2a3c8f61017
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905545"
---
# <a name="install-the-visual-studio-sdk"></a>Installieren des Visual Studio SDK

Das Visual Studio SDK (Software Development Kit) ist ein optionales Feature in Visual Studio-Setup. Sie können das vs SDK auch später installieren.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installieren Sie das Visual Studio SDK im Rahmen einer Visual Studio-Installation.

Wenn Sie das vs SDK in Ihre Visual Studio-Installation einbeziehen möchten, installieren Sie die Arbeitsauslastung für die **Visual Studio-Erweiterungs Entwicklung** unter **andere Toolsets**. Durch diese Arbeitsauslastung werden das Visual Studio SDK und die erforderlichen Voraussetzungen installiert. Sie können die Installation weiter optimieren, indem Sie die Option Komponenten in der **Zusammenfassungs** Ansicht auswählen oder deren Auswahl aufheben.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Installieren von Visual Studio SDK nach der Installation von Visual Studio

Um das Visual Studio SDK nach Abschluss der Installation von Visual Studio zu installieren, führen Sie den Visual Studio-Installer erneut aus, und wählen Sie die Arbeitsauslastung für die **Visual Studio-Erweiterungs Entwicklung**

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Installieren des Visual Studio SDK aus einer Projekt Mappe

Wenn Sie eine Projekt Mappe mit einem Erweiterbarkeits Projekt öffnen, ohne dass Sie zuvor das vs SDK installiert haben, werden Sie im Dialogfeld **fehlendes Feature installieren** aufgefordert, die Workloads für die **Visual Studio-Erweiterungs Entwicklung** zu installieren:

![Installieren der Erweiterungs Entwicklung](../extensibility/media/install-extension-development.png "Installieren der Erweiterungs Entwicklung")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Installieren Sie das Visual Studio SDK über die Befehlszeile.

Wie bei allen Visual Studio-Arbeits Auslastungen oder-Komponenten können Sie die Workloads für die **Visual Studio-Erweiterungs Entwicklung** (ID: Microsoft. VisualStudio. Workloads. visualstudioextension) auch über die Befehlszeile installieren. Ausführliche Informationen über die entsprechenden Befehls Zeilenschalter und allgemeine Anweisungen zum Bestimmen von Arbeits Auslastungs-oder Komponenten bezeichtern finden [Sie unter Verwenden von Befehlszeilen Parametern zum Installieren von Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) .

Beachten Sie, dass Sie den Visual Studio-Installer verwenden müssen, der mit der installierten Version von Visual Studio übereinstimmt. Wenn Sie z. b. Visual Studio Enterprise auf dem Computer installiert haben, müssen Sie den Visual Studio Enterprise Installer (*vs_enterprise.exe*) ausführen.
