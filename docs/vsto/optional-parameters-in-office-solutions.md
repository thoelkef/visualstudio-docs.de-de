---
title: "Optionale Parameter in Office-L&#246;sungen"
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
  - "Anwendungsentwicklung [Office-Entwicklung in Visual Studio], Optionale Parameter"
  - "Fehlendes Feld [Office-Entwicklung in Visual Studio]"
  - "Office-Anwendungen [Office-Entwicklung in Visual Studio], Optionale Parameter"
  - "Optionale Parameter [Office-Entwicklung in Visual Studio]"
  - "Parameter [Office-Entwicklung in Visual Studio], Optional"
  - "Visual Basic [Office-Entwicklung in Visual Studio], Optionale Parameter"
  - "Visual C# [Office-Entwicklung in Visual Studio], Optionale Parameter"
ms.assetid: 109eaef6-08bb-4b59-a29e-921f856027cc
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Optionale Parameter in Office-L&#246;sungen
  Viele der Methoden in den Objektmodellen von Microsoft Office\-Anwendungen akzeptieren optionale Parameter.  Wenn Sie mithilfe von Visual Basic eine Office\-Lösung in Visual Studio entwickeln, muss kein Wert für optionale Parameter übergeben werden, da die Standardwerte automatisch für jeden fehlenden Parameter verwendet werden.  In den meisten Fällen können optionale Parameter in Visual C\#\-Projekten auch weggelassen werden. Sie können jedoch keine optionalen **ref**\-Parameter der `ThisDocument`\-Klasse in Word\-Projekten auf Dokumentebene weglassen.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Weitere Informationen zur Verwendung von optionalen Parametern in Visual C\#\- und Visual Basic\-Projekten finden Sie unter [Benannte und optionale Argumente &#40;C&#35;-Programmierhandbuch&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) und [Optional Parameters &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  In früheren Versionen von Visual Studio müssen Sie einen Wert für jeden optionalen Parameter in Visual C\#\-Projekten übergeben.  Zur Vereinfachung schließen diese Projekte eine globale Variable mit dem Namen `missing` ein, die Sie an einen optionalen Parameter übergeben können, wenn Sie den Standardwert des Parameters verwenden möchten.  Visual C\#\-Projekte für Office in Visual Studio schließen nach wie vor die `missing`\-Variable ein. Diese ist jedoch in der Regel nicht erforderlich, wenn Sie Office\-Lösungen in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] entwickeln, es sei denn, Sie rufen Methoden mit optionalen **ref**\-Parametern in der `ThisDocument`\-Klasse in Projekten auf Dokumentebene für Word auf.  
  
## Beispiel in Excel  
 Die <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A>\-Methode verfügt über viele optionale Parameter.  Sie können Werte für einige Parameter angeben und den Standardwert von anderen Parametern übernehmen \(siehe folgendes Codebeispiel\).  Dieses Beispiel erfordert ein Projekt auf Dokumentebene mit einer Arbeitsblattklasse mit dem Namen `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/VB/Sheet1.vb#1)]  
  
## Beispiel in Word  
 Die <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>\-Methode verfügt über viele optionale Parameter.  Sie können Werte für einige Parameter angeben und den Standardwert von anderen Parametern übernehmen \(siehe folgendes Codebeispiel\).  
  
 [!code-csharp[Trin_VstrefGeneralWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstrefGeneralWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/VB/ThisDocument.vb#1)]  
  
## Verwenden von optionalen Parametern von Methoden in der ThisDocument\-Klasse in Visual C\#\-Projekten auf Dokumentebene für Word  
 Das Word\-Objektmodell enthält zahlreiche Methoden mit optionalen **ref**\-Parametern, die <xref:System.Object>\-Werte akzeptieren.  Optionale **ref**\-Parameter von Methoden der generierten `ThisDocument`\-Klasse können in Visual C\#\-Projekten auf Dokumentebene für Word jedoch nicht weggelassen werden.  Visual C\# ermöglicht es Ihnen, optionale **ref**\-Parameter nur für Methoden von Schnittstellen, jedoch nicht von Klassen, wegzulassen.  Das folgende Codebeispiel kann z. B. nicht kompiliert werden, da Sie keine optionalen **ref**\-Parameter der <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A>\-Methode der `ThisDocument`\-Klasse weglassen können.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#3)]  
  
 Wenn Sie Methoden der `ThisDocument`\-Klasse aufrufen, befolgen Sie diese Richtlinien:  
  
-   Übergeben Sie die **ref**\-Variable an den Parameter, um den Standardwert eines optionalen `missing`\-Parameters zu akzeptieren.  Die `missing`\-Variable wird automatisch in Visual C\# Office\-Projekten definiert und dem <xref:System.Type.Missing>\-Wert im generierten Projektcode zugewiesen.  
  
-   Um einen eigenen Wert für einen optionalen **ref**\-Parameter anzugeben, deklarieren Sie ein Objekt, das dem Wert zugewiesen wird, den Sie angeben möchten, und übergeben Sie dann das Objekt an den Parameter.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie die <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A>\-Methode aufgerufen wird, indem ein Wert für den *ignoreUppercase*\-Parameter angegeben und der Standardwert für die anderen Parameter akzeptiert wird.  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#4)]  
  
 Wenn Sie Code schreiben möchten, in dem optionale **ref**\-Parameter einer Methode in der `ThisDocument`\-Klasse weggelassen werden, können Sie die gleiche Methode alternativ auf dem von der <xref:Microsoft.Office.Interop.Word.Document>\-Eigenschaft zurückgegebenen <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A>\-Objekt aufrufen und die Parameter in dieser Methode weglassen.  Dies ist möglich, da <xref:Microsoft.Office.Interop.Word.Document> eine Schnittstelle und keine Klasse ist.  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#5)]  
  
 Weitere Informationen zu Wert\- und Referenztypparametern finden Sie unter [Passing Arguments by Value and by Reference &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) \(für Visual Basic\) und [Übergeben von Parametern &#40;C&#35;-Programmierhandbuch&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Siehe auch  
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)  
  
  