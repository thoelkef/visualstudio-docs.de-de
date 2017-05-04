---
title: "Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Dokumente [Office-Entwicklung in Visual Studio], Verwalten auf einem Server"
  - "Office-Dokumente [Office-Entwicklung in Visual Studio], Verwalten auf einem Server"
  - "ServerDocument-Klasse, Verwalten von Dokumenten auf einem Server"
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse
  Mit der ServerDocument\-Klasse in der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] können Sie mehrere Aspekte von Anpassungen auf Dokumentebene verwalten, selbst wenn Microsoft Office Word und Microsoft Office Excel nicht installiert sind.  Sie können die folgenden Aufgaben ausführen:  
  
-   Zugreifen auf und Ändern von Daten im Datencache eines Dokuments oder einer Arbeitsmappe.  Weitere Informationen finden Sie unter [Arbeiten mit im Dokument zwischengespeicherten Daten](#CachedData).  
  
-   Verwalten der Anpassungsassembly, die einem Dokument zugeordnet ist.  Weitere Informationen finden Sie unter [Verwalten der Dokumentanpassung](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Die ServerDocument\-Klasse  
 Die ServerDocument\-Klasse kann auf Computern verwendet werden, auf denen Office nicht installiert ist.  Daher wird diese Klasse üblicherweise in Anwendungen verwendet, die nicht in Office integriert sind, z. B. Konsolenprojekte oder Windows Forms\-Projekte, im Gegensatz zu Office\-Projekten.  Verwenden Sie die Assembly <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> class in the Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 Die ServerDocument\-Klasse kann für Anpassungen auf Dokumentebene verwendet werden, die mit [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] erstellt wurden.  
  
 Weitere Informationen zu Visual Studio 2010\-Tools für Office\-Laufzeit und Office\-Erweiterungen für .NET Framework finden Sie unter [Übersicht über die Visual Studio Tools for Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Wenn Sie über eine Legacyversion einer Anwendung verfügen, die die ServerDocument\-Klasse in Visual Studio\-Tools für Office System \(Laufzeit, Version 3.0\) verwendet, muss Visual Studio\-Tools für Office System \(Laufzeit, Version 3.0\) auf den Computern installiert werden, die die Anwendung ausführen.  Visual Studio 2010\-Tools für Office\-Laufzeit kann diese Anwendungen nicht ausführen.  
  
##  <a name="CachedData"></a> Arbeiten mit im Dokument zwischengespeicherten Daten  
 Die ServerDocument\-Klasse stellt Member bereit, die Sie verwenden können, um mit dem Datencache in angepassten Dokumenten zu arbeiten.  Weitere Informationen über zwischengespeicherte Daten finden Sie unter [Zwischenspeichern von Daten](../vsto/caching-data.md) und unter [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 In der folgenden Tabelle werden die Member aufgeführt, die Sie verwenden können, um mit zwischengespeicherten Daten zu arbeiten.  
  
|Aufgabe|Zu verwendender Member|  
|-------------|----------------------------|  
|Bestimmen, ob ein Dokument über einen Datencache verfügt|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A>\-Methode|  
|Zugreifen auf die zwischengespeicherten Daten in einem Dokument<br /><br /> Weitere Informationen finden Sie unter [Zugreifen auf Daten in Dokumenten auf dem Server](../vsto/accessing-data-in-documents-on-the-server.md).|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A>\-Eigenschaft|  
  
##  <a name="CustomizationInfo"></a> Verwalten der Dokumentanpassung  
 Sie können Member der ServerDocument\-Klasse zum Verwalten der Anpassungsassembly verwenden, die einem Dokument zugeordnet ist.  Sie können z. B. die Anpassung aus einem Dokument programmgesteuert entfernen, sodass das Dokument nicht mehr Teil einer Anpassung ist.  
  
 In der folgenden Tabelle werden die Member, mit denen Sie die Anpassungsassembly verwalten können, aufgeführt.  
  
|Aufgabe|Zu verwendender Member|  
|-------------|----------------------------|  
|Ermitteln, ob ein Dokument Teil einer Anpassung auf Dokumentebene ist|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A>\-Methode|  
|Programmgesteuertes Anfügen einer Anpassung an ein Dokument zur Laufzeit<br /><br /> Weitere Informationen finden Sie unter [Gewusst wie: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Eine der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>\-Methoden|  
|Programmgesteuertes Entfernen einer Anpassung aus einem Dokument zur Laufzeit<br /><br /> Weitere Informationen finden Sie unter [Gewusst wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>\-Methode|  
|Abrufen der URL des Bereitstellungsmanifests, das dem Dokument zugeordnet ist|Die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A>\-Eigenschaft|  
  
## Siehe auch  
 [Gewusst wie: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Gewusst wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Übersicht über die Visual Studio Tools for Office-Laufzeit](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Zwischenspeichern von Daten](../vsto/caching-data.md)  
  
  