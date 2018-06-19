---
title: Installieren von Visual Studio SDK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 259646e0dbee4831db83a7098954d1c5144d8ead
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129075"
---
# <a name="installing-the-visual-studio-sdk"></a>Installieren von Visual Studio SDK
Das Visual Studio SDK ist ein optionales Feature in Visual Studio-Setup. Sie können das VS-SDK auch später installieren.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installieren von Visual Studio SDK als Teil einer Installation von Visual Studio  
 Wenn Sie VSSDK in Visual Studio-Installation aufnehmen möchten, müssen Sie installieren die **Development für Visual Studio-Erweiterung** Arbeitsauslastung unter **andere Toolsets**. Dadurch wird das Visual Studio SDK als auch die erforderlichen Komponenten installiert. Sie können die Installation weiter anpassen, indem Sie auswählen, oder deren Auswahl aufheben Komponenten in der Zusammenfassung anzuzeigen. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Installieren von Visual Studio SDK nach der Installation von Visual Studio  
 Wenn Sie das Visual Studio SDK nach Abschluss der Installation von Visual Studio installieren möchten, führen Sie die Visual Studio-Installer erneut aus, und wählen Sie die **Development für Visual Studio-Erweiterung** Arbeitsauslastung.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Installieren von Visual Studio SDK aus einer Projektmappe  
 Wenn Sie eine Projektmappe mit einem-Erweiterungsprojekt öffnen, ohne zuvor zu installieren VSSDK, werden Sie durch eine hervorgehobene Informationsleiste oben im Projektmappen-Explorer aufgefordert werden. Es sollte etwa wie folgt aussehen:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Installieren von Visual Studio SDK über die Befehlszeile  
Mit einem Visual Studio-Arbeitsauslastung oder einer Komponente, installieren Sie auch können die **Development für Visual Studio-Erweiterung** Arbeitslast (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) über die Befehlszeile. Finden Sie unter [Befehlszeilenparameter verwenden, um Visual Studio installieren](../install/use-command-line-parameters-to-install-visual-studio.md) ausführliche Informationen zu den entsprechenden Befehlszeilenoptionen und allgemeine Anweisungen zum Ermitteln der Arbeitsauslastung oder Komponente Bezeichner.
  
 Beachten Sie, dass Sie Visual Studio-Installationsprogramm verwenden müssen, das die installierte Version von Visual Studio entspricht. Wenn Sie Visual Studio Enterprise auf Ihrem Computer installiert haben, müssen Sie das Installationsprogramm für Visual Studio Enterprise (vs_enterprise.exe) ausführen.