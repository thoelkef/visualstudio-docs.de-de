---
title: "Bereitstellen einer Office-Lösung | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
ms.assetid: 4cdf4bc6-72c5-4166-8019-d5fd61281079
caps.latest.revision: "78"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8c22db51700a711bed0edd2d5a8431d6dc64c281
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-an-office-solution"></a>Bereitstellen einer Office-Projektmappe
  Sie können Office-Lösungen mit ClickOnce oder Windows Installer bereitstellen. Mit ClickOnce verringern Sie die Anzahl von Schritten, die zum Bereitstellen und Aktualisieren der Lösung erforderlich sind. Wenn Sie Windows Installer verwenden, haben Sie die Kontrolle darüber, wie eine Lösung installiert wird und welche Informationen das Setupprogramm anzeigt, wenn der Benutzer die Lösung installiert.  
  
> [!NOTE]  
>  Bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern "interested" [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins haben einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.  
  
## <a name="deploying-a-solution-by-using-clickonce"></a>Bereitstellen einer Lösung mit ClickOnce  
 Wenn Sie eine Lösung mit ClickOnce bereitstellen, veröffentlichen Sie diese an einem zentralen Speicherort, wo Benutzer sie installieren und ausführen können. Sie können die Lösung aktualisieren, ohne an die Benutzer ein neues Setupprogramm verteilen zu müssen.  Diese Bereitstellungsoption ist einfacher, aber Sie können dem Benutzer bei der Installation keine speziellen Informationsseiten anzeigen. Außerdem müssen Lösungen mehrmals installiert werden, wenn auf dem Computer mehrere Benutzer eingerichtet sind. Finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="deploying-a-solution-by-using-windows-installer"></a>Bereitstellen einer Lösung mit Windows Installer  
 Wenn Sie eine Lösung mit Windows Installer bereitstellen, verteilen Sie ein Setupprogramm an Benutzer, und diese installieren die Lösung, indem sie das Setupprogramm verwenden. Das Setupprogramm kann eine Lösung sowohl einzeln für den aktuellen Benutzer als auch gleichzeitig für alle Benutzer eines Computers installieren. Sie haben auch etwas mehr Kontrolle über die Optionen, die für Benutzer bei der Installation angezeigt werden. Beispielsweise können Sie eine Lizenzvereinbarung anzeigen oder es dem Benutzer ermöglichen, bestimmte Komponenten einer Lösung zu installieren. Wenn Sie die Lösung aktualisieren, müssen Sie ein neues Setupprogramm verteilen. Finden Sie unter [Bereitstellen einer Office-Projektmappe mit Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Bereitstellen einer Office-Projektmappe mit Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Problembehandlung bei der Office-Projektmappenbereitstellung](../vsto/troubleshooting-office-solution-deployment.md)  
  
  