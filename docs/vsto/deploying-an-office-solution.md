---
title: Bereitstellen einer Office-Lösung
ms.date: 08/14/2019
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24ec10c42935ac961218f910fbef98d51f5f5569
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416509"
---
# <a name="deploy-an-office-solution"></a>Bereitstellen einer Office-Lösung
  Sie können Office-Lösungen mit ClickOnce oder Windows Installer bereitstellen. Mit ClickOnce verringern Sie die Anzahl von Schritten, die zum Bereitstellen und Aktualisieren der Lösung erforderlich sind. Wenn Sie Windows Installer verwenden, haben Sie die Kontrolle darüber, wie eine Lösung installiert wird und welche Informationen das Setupprogramm anzeigt, wenn der Benutzer die Lösung installiert.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="deploy-a-solution-by-using-clickonce"></a>Bereitstellen einer Lösung mithilfe von ClickOnce
 Wenn Sie eine Lösung mit ClickOnce bereitstellen, veröffentlichen Sie diese an einem zentralen Speicherort, wo Benutzer sie installieren und ausführen können. Sie können die Lösung aktualisieren, ohne an die Benutzer ein neues Setupprogramm verteilen zu müssen.  Diese Bereitstellungsoption ist einfacher, aber Sie können dem Benutzer bei der Installation keine speziellen Informationsseiten anzeigen. Außerdem müssen Lösungen mehrmals installiert werden, wenn auf dem Computer mehrere Benutzer eingerichtet sind. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploy-a-solution-by-using-windows-installer"></a>Bereitstellen einer Lösung mithilfe von Windows Installer
 Wenn Sie eine Lösung mit Windows Installer bereitstellen, verteilen Sie ein Setupprogramm an Benutzer, und diese installieren die Lösung, indem sie das Setupprogramm verwenden. Das Setupprogramm kann eine Lösung sowohl einzeln für den aktuellen Benutzer als auch gleichzeitig für alle Benutzer eines Computers installieren. Sie haben auch etwas mehr Kontrolle über die Optionen, die für Benutzer bei der Installation angezeigt werden. Beispielsweise können Sie eine Lizenzvereinbarung anzeigen oder es dem Benutzer ermöglichen, bestimmte Komponenten einer Lösung zu installieren. Wenn Sie die Lösung aktualisieren, müssen Sie ein neues Setupprogramm verteilen. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung mithilfe von Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="see-also"></a>Weitere Informationen
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
- [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Bereitstellen einer Office-Lösung mithilfe von Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)
- [Fehlerbehebung bei der Bereitstellung von Office-Lösungen](../vsto/troubleshooting-office-solution-deployment.md)
