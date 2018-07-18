---
title: 'Gewusst wie: Öffnen Office-Projektmappen ohne Ausführen von Code'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f7ced7b38a4f32d96b397e7f9eebb1d40be03ae3
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254987"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Gewusst wie: Öffnen Office-Projektmappen ohne Ausführen von Code
  Mit Erweiterungen durch verwalteten Code erstellte eine Microsoft Office-Projektmappe ausgeführt wird, auch wenn die sicherheitseinstellung in der Endbenutzer Office-Anwendung auf hoch festgelegt ist. Dies ist da die Sicherheit von Microsoft .NET Framework, nicht von Microsoft Office verwaltet wird.  
  
 Es gibt jedoch auch vorkommen, dass Sie möglicherweise ein Dokument zu öffnen, ohne den Code ausführen möchten. Z. B. Code, der ausgeführt wird, wenn das Dokument geöffnet wird, kann den Inhalt ändern, aber die Möglichkeit, die das Dokument vor den Änderungen am Code hierfür, aktualisiert werden soll. Oder möglicherweise möchten das Dokument mit der bestimmte Informationen darin an jemanden senden, und nicht möchten, dass des Codes zum Ausführen und den Inhalt möglicherweise ändern.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Es gibt mehrere Möglichkeiten, ein Dokument oder eine Arbeitsmappe mit Erweiterungen durch verwalteten Code ohne Ausführung von Code für die Assembly zu öffnen.  
  
## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>So umgehen Sie die Assembly mithilfe der UMSCHALT-Taste  
  
-   Öffnen von Dokumenten und Arbeitsmappen aus der **Datei** Menü bei gedrückter der **UMSCHALT** Schlüssel, um zu verhindern, dass Word und Excel Initialisierungsereignisse auslösen, während das Dokument geöffnet wird.  
  
    > [!NOTE]  
    >  Wenn Sie ein Dokument oder eine Arbeitsmappe öffnen die **Einstieg** Aufgabenbereich gedrückt **UMSCHALT** wird den Code nicht umgangen. Darüber hinaus verhindert die UMSCHALTTASTE gedrückt gehalten nicht Ereignisse ausgelöst werden, nachdem das Dokument geöffnet ist.  
  
     Diese Methode ist nützlich, wenn Sie ein Dokument, um Änderungen vorzunehmen, ohne den Code ausführen und ändern zunächst das Dokument öffnen möchten.  
  
## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Um eine Assembly zu umgehen, indem Sie das Umbenennen oder entfernen  
  
-   Wenn Sie die erforderlichen Berechtigungen auf dem Computer haben, in dem die Assembly befindet, können Sie umbenennen oder entfernen Sie die Assembly, sodass das Dokument oder die Arbeitsmappe gefunden werden kann. Dadurch wird ein Fehler ausgelöst wird, jedes Mal, wenn das Office-Dokument geöffnet wird.  
  
     Wenn die Lösung von mehreren Personen verwendet wird, verhindert diese Methode die Projektmappe ausgeführt wird für alle. Dies kann nützlich sein, wenn ein Problem, im Code oder einem Server auf die verwiesen wird gefunden wird, und Sie alle Benutzer aus der Ausführung beenden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)   
 [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  