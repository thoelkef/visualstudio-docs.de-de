---
title: Installieren von Visual Studio SDK | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 17b3b0a107d263a213746a625ec5a65419695b4d
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
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