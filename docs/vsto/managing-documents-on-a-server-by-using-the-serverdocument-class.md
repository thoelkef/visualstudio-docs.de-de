---
title: Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f776b73b4f80756a36a5ad4610a60440a6f9abd1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876069"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse
  Können Sie die `ServerDocument` -Klasse in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] mehrere Aspekte von Anpassungen auf Dokumentebene, zu verwalten, auch wenn Microsoft Office Word und Microsoft Office Excel nicht installiert werden. Sie können die folgenden Aufgaben ausführen:  
  
- Zugreifen auf und Ändern von Daten im Datencache eines Dokuments oder einer Arbeitsmappe. Weitere Informationen finden Sie unter [arbeiten mit im Dokument zwischengespeicherten Daten](#CachedData).  
  
- Verwalten der Anpassungsassembly, die einem Dokument zugeordnet ist. Weitere Informationen finden Sie unter [Verwalten der dokumentanpassung](#CustomizationInfo).  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>Verstehen der ServerDocument-Klasse  
 Die `ServerDocument`-Klasse kann auf Computern verwendet werden, auf denen Office nicht installiert ist. Daher wird diese Klasse üblicherweise in Anwendungen verwendet, die nicht in Office integriert sind, z. B. Konsolenprojekte oder Windows Forms-Projekte, im Gegensatz zu Office-Projekten. Verwenden der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> -Klasse in der *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* Assembly.  
  
 Die `ServerDocument`-Klasse kann für Anpassungen auf Dokumentebene verwendet werden, die mit [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] erstellt wurden.  
  
 Weitere Informationen zu Visual Studio 2010-Tools für Office-Laufzeit und die Office-Erweiterungen für .NET Framework finden Sie unter [Visual Studio-Tools für Office-laufzeitübersicht](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Wenn Sie eine ältere Anwendung verfügen, verwendet der `ServerDocument` -Klasse in der `Visual Studio Tools for Office` System (Version 3.0 Common Language Runtime), wird die `Visual Studio Tools for Office` System (Version 3.0 Runtime) muss installiert sein, auf Computern, auf denen die Anwendung ausgeführt. Die `Visual Studio 2010 Tools for Office runtime` dieser Anwendungen kann nicht ausgeführt werden.  
  
##  <a name="CachedData"></a> Arbeiten Sie mit im Dokument zwischengespeicherten Daten  
 Die `ServerDocument`-Klasse stellt Member bereit, die Sie verwenden können, um mit dem Datencache in angepassten Dokumenten zu arbeiten. Weitere Informationen über zwischengespeicherte Daten finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md) und [Zugriff auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 In der folgenden Tabelle werden die Member aufgeführt, die Sie verwenden können, um mit zwischengespeicherten Daten zu arbeiten.  
  
|Aufgabe|Zu verwendender Member|  
|----------|-------------------|  
|Bestimmen, ob ein Dokument über einen Datencache verfügt|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> -Methode.|  
|Zugreifen auf die zwischengespeicherten Daten in einem Dokument<br /><br /> Weitere Informationen finden Sie unter [Zugriff auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>-Eigenschaft|  
  
##  <a name="CustomizationInfo"></a> Verwalten der dokumentanpassung  
 Sie können Member der `ServerDocument`-Klasse zum Verwalten der Anpassungsassembly verwenden, die einem Dokument zugeordnet ist. Sie können z. B. die Anpassung aus einem Dokument programmgesteuert entfernen, sodass das Dokument nicht mehr Teil einer Anpassung ist.  
  
 In der folgenden Tabelle werden die Member, mit denen Sie die Anpassungsassembly verwalten können, aufgeführt.  
  
|Aufgabe|Zu verwendender Member|  
|----------|-------------------|  
|Ermitteln, ob ein Dokument Teil einer Anpassung auf Dokumentebene ist|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> -Methode.|  
|Eine Anpassung zu einem Dokument zur Laufzeit programmgesteuert zu anzufügen.<br /><br /> Weitere Informationen finden Sie unter [Vorgehensweise: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Eine der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>-Methoden|  
|Programmgesteuertes Entfernen einer Anpassung aus einem Dokument zur Laufzeit<br /><br /> Weitere Informationen finden Sie unter [Vorgehensweise: Entfernen von verwaltetem Code-Erweiterungen aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> -Methode.|  
|Abrufen der URL des Bereitstellungsmanifests, das dem Dokument zugeordnet ist|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>-Eigenschaft|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Vorgehensweise: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio-Tools für Office-laufzeitübersicht](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Zwischenspeichern von Daten](../vsto/caching-data.md)  
