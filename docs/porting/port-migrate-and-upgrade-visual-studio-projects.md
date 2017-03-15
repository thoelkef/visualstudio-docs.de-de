---
title: "Übertragung, Migration und Upgrade der Visual Studio-Projekte | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/16/2016
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ae6564f10ca561853444698665779bd1014d4afd
ms.openlocfilehash: 2915a9ceec638471ac29599992a7ccdff17cefb4
ms.lasthandoff: 02/22/2017

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Übertragung, Migration und Upgrade der Visual Studio-Projekte
Wenn Sie auf eine neuere Version von Visual Studio upgraden, sollten Sie wissen, ob Sie eine der Lösungen, Projekte, Dateien und anderen Objekte ändern müssen, die Sie in früheren Versionen erstellt haben, *bevor* Sie sie in den neuesten Versionen ausführen.

 Viele häufig verwendete Ressourcen verhalten sich in unserer neuesten Version Visual Studio 2017 RC wie in unserer aktuellen Version Visual Studio 2015. Sie werden sich auch in unseren früheren Versionen Visual Studio 2013 und Visual Studio 2012 so verhalten.

 In Visual Studio 2017 RC können Sie beispielsweise ein Projekt öffnen, das in Visual Studio 2015 oder Visual Studio 2013 erstellt wurde. Sie können es ändern und erneut in Visual Studio 2017 RC öffnen. Ihre Änderungen bleiben erhalten und das Projekt verhält sich ebenso wie in der vorherigen Version. Dies gilt auch für viele Ressourcen, die in Visual Studio 2012 erstellt wurden.  

 Wenn Sie Visual Studio 2015 mit Visual Studio 2013, Visual Studio 2012 oder Visual Studio 2010 SP1 verwenden, können Sie Projekte und Dateien in jeder dieser Versionen erstellen und ändern. Sie können Projekte und Dateien zwischen den Versionen übertragen, solange Sie keine Funktionen hinzufügen, die nicht von einer der Versionen unterstützt werden. (Weitere Informationen über die Funktionen, die spezifisch für die jeweiligen Versionen sind, finden Sie in [Versionshinweise](https://www.visualstudio.com/vs/release-notes/).)

