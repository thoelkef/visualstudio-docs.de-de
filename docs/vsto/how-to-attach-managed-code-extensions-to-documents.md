---
title: "Gewusst wie: Anf&#252;gen von Erweiterungen durch verwalteten Code an Dokumente"
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
  - "Dokumente [Office-Entwicklung in Visual Studio], Verwaltete Codeerweiterungen"
  - "Erweiterungen durch verwalteten Code [Office-Entwicklung in Visual Studio], Anhängen"
ms.assetid: b38c3a35-8b4a-4e86-8475-88fa8a873a5d
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Gewusst wie: Anf&#252;gen von Erweiterungen durch verwalteten Code an Dokumente
  Sie können eine Anpassungsassembly an ein vorhandenes Microsoft Office Word\-Dokument oder eine vorhandene Microsoft Office Excel\-Arbeitsmappe anfügen.  Das Dokument oder die Arbeitsmappe können in jedem Dateiformat vorliegen, das von den Microsoft Office\-Projekten und die Entwicklungstools von Visual Studio unterstützt wird.  Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Verwenden Sie zum Anfügen einer Anpassung an ein Word\- oder Excel\-Dokument die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>\-Methode der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse.  Da die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse für die Ausführung auf einem Computer konzipiert ist, auf dem Microsoft Office nicht installiert ist, können Sie diese Methode in Lösungen verwenden, die sich nicht direkt auf Microsoft Office\-Entwicklung beziehen, z. B. eine Konsolenanwendung oder Windows Forms\-Anwendung\).  
  
> [!NOTE]  
>  Falls vom Code erwartete Steuerelemente nicht im angegebenen Dokument enthalten ist, wird die Anpassung nicht geladen.  
  
 ![Link zu Video](~/data-tools/media/playvideo.gif "Link zu Video") Eine entsprechende Videodemo finden Sie im Thema zum [Anfügen oder Trennen einer VSTO\-Assembly an ein bzw. von einem Word\-Dokument](http://go.microsoft.com/fwlink/?LinkId=136782) \(möglicherweise in englischer Sprache\).  
  
### So hängen Sie Erweiterungen durch verwalteten Code an ein Dokument an  
  
1.  In einem Projekt, das nicht Microsoft Office, wie eine Konsolenanwendung oder ein Windows Forms\-Projekt erfordert, fügen Sie einen Verweis auf den Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll\- und Microsoft.VisualStudio.Tools.Applications.Runtime.dll\-Assemblys hinzu.  
  
2.  Fügen Sie am Anfang der Codedatei die folgende **Imports**\-Anweisung bzw. **using**\-Anweisung ein.  
  
     [!code-csharp[Trin_VstcoreDeployment#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#4)]  
  
3.  Rufen Sie die statische <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>\-Methode auf.  
  
     Im folgenden Codebeispiel wird die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A>\-Überladung verwendet.  Diese Überladung akzeptiert den vollständigen Pfad des Dokuments und einen <xref:System.Uri>, der den Speicherort des Bereitstellungsmanifests für die Anpassung angibt, die Sie an das Dokument anfügen möchten.  In diesem Beispiel wird davon ausgegangen, dass ein Word\-Dokument namens **WordDocument1.docx** sich auf dem Desktop befindet und dass das Bereitstellungsmanifest in einem Ordner namens **Publish** enthalten ist, der sich ebenfalls auf dem Desktop befindet.  
  
     [!code-csharp[Trin_VstcoreDeployment#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#3)]  
  
4.  Erstellen Sie das Projekt, und führen Sie die Anwendung auf dem Computer aus, auf dem Sie die Anpassung hinzufügen möchten.  Der Computer muss die Visual Studio 2010 Tools for Office\-Laufzeit installiert haben.  
  
## Siehe auch  
 [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Gewusst wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Anwendungs- und Bereitstellungsmanifeste in Office-Projektmappen](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  