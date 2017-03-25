---
title: Installieren das Visual Studio SDK | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 722c32c139d2f560fa6d10aba9fd8bac610f9f20
ms.lasthandoff: 03/07/2017

---
# <a name="installing-the-visual-studio-sdk"></a>Das Visual Studio SDK installieren
Das Visual Studio SDK ist eine optionale Funktion in Visual Studio-Setup. Sie können auch später im Visual Studio SDK installieren.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Installieren das Visual Studio SDK als Teil einer Visual Studio-Installation  
 Wenn Sie VSSDK in Visual Studio-Installation aufnehmen möchten, installieren Sie die **Visual Studio-Erweiterung Entwicklung** Arbeitslast unter **andere Toolsets**. Dadurch wird das Visual Studio SDK sowie die erforderlichen Komponenten installiert. Sie können die Installation weiter anpassen, indem Sie auswählen oder Aufheben der Auswahl von Komponenten in der Zusammenfassung anzuzeigen. 
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Installieren das Visual Studio SDK nach der Installation von Visual Studio  
 Wenn Sie das Visual Studio SDK nach Abschluss der Installation von Visual Studio installieren möchten, führen Sie die Visual Studio-Installer erneut aus, und wählen Sie die **Visual Studio-Erweiterung Entwicklung** Arbeitslast.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Installieren das Visual Studio SDK aus einer Projektmappe  
 Wenn Sie eine Lösung mit einem Erweiterbarkeitsprojekt öffnen, ohne die erste Installation VSSDK, werden Sie durch eine hervorgehobene Informationsleiste oben im Projektmappen-Explorer aufgefordert werden. Es sollte etwa wie folgt aussehen:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Installieren das Visual Studio SDK von der Befehlszeile aus  
Wie mit Visual Studio-Workload oder Komponente, können Sie auch den Artikel über die Befehlszeile installieren. Finden Sie unter [Befehlszeilenoptionen verwenden, um die Installation von Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) Einzelheiten zu den entsprechenden Befehlszeilenoptionen und die Bezeichner Arbeitslast oder Komponente zu bestimmen.
  
 Beachten Sie, dass Sie Visual Studio-Installationsprogramm verwenden müssen, das die installierte Version von Visual Studio entspricht. Wenn Sie Visual Studio Enterprise auf Ihrem Computer installiert haben, müssen Sie das Visual Studio Enterprise-Installationsprogramm (vs_enterprise.exe) ausführen.
