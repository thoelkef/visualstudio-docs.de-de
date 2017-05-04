---
title: "Gewusst wie: Anpassen an die mehrsprachige Benutzeroberfl&#228;che von Office | Microsoft Docs"
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
  - "Globalisierung [Office-Entwicklung in Visual Studio], Benutzeroberflächenfestlegung"
  - "Lokalisierung [Office-Entwicklung in Visual Studio], Benutzeroberflächenfestlegung"
  - "MUI [Office-Entwicklung in Visual Studio]"
  - "Mehrsprachige Benutzeroberfläche [Office-Entwicklung in Visual Studio]"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Globalisierung"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Lokalisierung"
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Gewusst wie: Anpassen an die mehrsprachige Benutzeroberfl&#228;che von Office
  Die mehrsprachige Benutzeroberfläche \(Multilingual User Interface, MUI\) ist ein Feature von Microsoft Office, das Endbenutzer in die Lage versetzt, die Sprache der Benutzeroberfläche zu ändern.  Beispielsweise kann ein Endbenutzer, der mit einer englischen Benutzeroberfläche arbeitet, die Sprache der Benutzeroberfläche in Spanisch ändern.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Wenn die Anwendung für Personen vorgesehen ist, die verschiedene Sprachen in Office verwenden, können Sie Code hinzufügen, der alle Zeichenfolgen der Benutzeroberfläche automatisch in die Sprache ändert, die auf dem Computer des Benutzers von Office verwendet wird \(wenn der Benutzer die erforderlichen Ressourcen installiert hat\).  
  
### So überprüfen Sie die aktuelle Einstellung für die Office\-Benutzeroberfläche  
  
1.  Verwenden Sie die <xref:System.Threading.Thread.CurrentUICulture%2A>\-Eigenschaft des aktuellen Threads.  Legen Sie die Sprache der Benutzeroberflächenzeichenfolgen auf die Sprache fest, die von der Office\-Version verwendet wird, welche derzeit auf dem Benutzercomputer ausgeführt wird.  
  
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreCreatingExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/Sheet1.vb#10)]  
  
## Siehe auch  
 [Verweisen auf Office-Anwendungen durch primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Späte Bindung in Office-Lösungen](../vsto/late-binding-in-office-solutions.md)  
  
  