---
title: Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse | Microsoft Docs
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
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2120e7c70abaddd4f51c0214a2c5ae517cf955cc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="managing-documents-on-a-server-by-using-the-serverdocument-class"></a>Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse
  Können Sie die ServerDocument-Klasse in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verschiedener Aspekte von Anpassungen auf Dokumentebene verwalten, auch wenn Microsoft Office Word und Microsoft Office Excel nicht installiert sind. Sie können die folgenden Aufgaben ausführen:  
  
-   Zugreifen auf und Ändern von Daten im Datencache eines Dokuments oder einer Arbeitsmappe. Weitere Informationen finden Sie unter [arbeiten mit im Dokument zwischengespeicherten Daten](#CachedData).  
  
-   Verwalten der Anpassungsassembly, die einem Dokument zugeordnet ist. Weitere Informationen finden Sie unter [Verwalten der Dokumentanpassung](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understanding-the-serverdocument-class"></a>Die ServerDocument-Klasse  
 Die ServerDocument-Klasse dient zur auf Computern verwendet werden, die nicht Office installiert ist. Daher wird diese Klasse üblicherweise in Anwendungen verwendet, die nicht in Office integriert sind, z. B. Konsolenprojekte oder Windows Forms-Projekte, im Gegensatz zu Office-Projekten. Verwenden Sie die Assembly <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> class in the Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 Die ServerDocument-Klasse, Vorgänge für Anpassungen auf Dokumentebene, die erstellt wurden, genutzt werden [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Weitere Informationen zu Visual Studio 2010-Tools für Office-Laufzeit und die Office-Erweiterungen für .NET Framework, finden Sie unter [Visual Studio-Tools für Office-Laufzeitübersicht](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Wenn Sie eine ältere Anwendung verfügen, die die ServerDocument-Klasse in Visual Studio-Tools für Office-System verwendet (Version 3.0 Common Language Runtime), der Visual Studio-Tools für Office System (Version 3.0 Runtime) muss auf Computern installiert werden, auf denen die Anwendung ausgeführt. Visual Studio 2010-Tools für Office-Laufzeit kann diese Anwendungen nicht ausführen.  
  
##  <a name="CachedData"></a>Arbeiten mit im Dokument zwischengespeicherten Daten  
 Die ServerDocument-Klasse enthält Elemente, die Sie verwenden können, um mit dem Datencache in angepassten Dokumenten zu arbeiten. Weitere Informationen über zwischengespeicherte Daten finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md) und [zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 In der folgenden Tabelle werden die Member aufgeführt, die Sie verwenden können, um mit zwischengespeicherten Daten zu arbeiten.  
  
|Aufgabe|Zu verwendender Member|  
|----------|-------------------|  
|Bestimmen, ob ein Dokument über einen Datencache verfügt|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>-Methode.|  
|Zugreifen auf die zwischengespeicherten Daten in einem Dokument<br /><br /> Weitere Informationen finden Sie unter [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md).|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>-Eigenschaft|  
  
##  <a name="CustomizationInfo"></a>Verwalten der Dokumentanpassung  
 Mitglieder der ServerDocument-Klasse können Sie die Anpassungsassembly verwalten, die einem Dokument zugeordnet ist. Sie können z. B. die Anpassung aus einem Dokument programmgesteuert entfernen, sodass das Dokument nicht mehr Teil einer Anpassung ist.  
  
 In der folgenden Tabelle werden die Member, mit denen Sie die Anpassungsassembly verwalten können, aufgeführt.  
  
|Aufgabe|Zu verwendender Member|  
|----------|-------------------|  
|Ermitteln, ob ein Dokument Teil einer Anpassung auf Dokumentebene ist|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>-Methode.|  
|Programmgesteuertes Anfügen einer Anpassung an ein Dokument zur Laufzeit<br /><br /> Weitere Informationen finden Sie unter [wie: Anfügen Managed Code Extensions zu Dokumenten](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Eine der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>-Methoden|  
|Programmgesteuertes Entfernen einer Anpassung aus einem Dokument zur Laufzeit<br /><br /> Weitere Informationen finden Sie unter [Vorgehensweise: Entfernen Managed Code Extensions aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>-Methode.|  
|Abrufen der URL des Bereitstellungsmanifests, das dem Dokument zugeordnet ist|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>-Eigenschaft|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Vorgehensweise: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Zwischenspeichern von Daten](../vsto/caching-data.md)  
  