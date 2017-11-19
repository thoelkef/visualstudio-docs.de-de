---
title: Optionale Parameter in Office-Projektmappen | Microsoft Docs
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
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
ms.assetid: 109eaef6-08bb-4b59-a29e-921f856027cc
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4293d13ffc5b69c23c0b613a3d9747248d6fa790
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="optional-parameters-in-office-solutions"></a>Optionale Parameter in Office-Lösungen
  Viele der Methoden in den Objektmodellen von Microsoft Office-Anwendungen akzeptieren optionale Parameter. Wenn Sie mithilfe von Visual Basic eine Office-Lösung in Visual Studio entwickeln, muss kein Wert für optionale Parameter übergeben werden, da die Standardwerte automatisch für jeden fehlenden Parameter verwendet werden. In den meisten Fällen können Sie optionale Parameter in Visual C#-Projekten auch weggelassen. Nicht jedoch optionale weggelassen **Ref** Parameter von der `ThisDocument` -Klasse im Word-Projekten auf Dokumentebene.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Weitere Informationen zum Arbeiten mit optionalen Parametern in Visual c# und Visual Basic-Projekten finden Sie unter [benannte und optionale Argumente &#40; C &#35; Programmierhandbuch &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) und [optionale Parameter &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  In früheren Versionen von Visual Studio müssen Sie einen Wert für jeden optionalen Parameter in Visual C#-Projekten übergeben. Zur Vereinfachung schließen diese Projekte eine globale Variable mit dem Namen `missing` ein, die Sie an einen optionalen Parameter übergeben können, wenn Sie den Standardwert des Parameters verwenden möchten. Visual C#-Projekte für Office in Visual Studio schließen nach wie vor die `missing` Variable, aber Sie müssen normalerweise nicht beim Entwickeln von Office-Projektmappen in Verwendung [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], außer beim Aufrufen von Methoden mit optionalen **Ref** Parameter in der `ThisDocument` -Klasse in Projekten auf Dokumentebene für Word.  
  
## <a name="example-in-excel"></a>Beispiel in Excel  
 Die <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A>-Methode verfügt über viele optionale Parameter. Sie können Werte für einige Parameter angeben und den Standardwert von anderen Parametern übernehmen (siehe folgendes Codebeispiel). Dieses Beispiel erfordert ein Projekt auf Dokumentebene mit einer Arbeitsblattklasse mit dem Namen `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]  
  
## <a name="example-in-word"></a>Beispiel in Word  
 Die <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>-Methode verfügt über viele optionale Parameter. Sie können Werte für einige Parameter angeben und den Standardwert von anderen Parametern übernehmen (siehe folgendes Codebeispiel).  
  
 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]  
  
## <a name="using-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Verwenden von optionalen Parametern von Methoden in der ThisDocument-Klasse in Visual C#-Projekten auf Dokumentebene für Word  
 Word-Objektmodell enthält zahlreiche Methoden mit optionalen **Ref** Parameter, akzeptieren <xref:System.Object> Werte. Nicht jedoch optionale weggelassen **Ref** Parameter der Methoden der generierten `ThisDocument` Klasse in Visual C#-Projekten auf Dokumentebene für Word. Visual c# ermöglicht es Ihnen, optional weglassen **Ref** Parameter nur für Methoden von Schnittstellen, jedoch nicht von Klassen. Z. B. im folgenden Codebeispiel wird nicht kompiliert werden, da Sie optional weglassen können **Ref** Parameter von der <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> Methode der `ThisDocument` Klasse.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]  
  
 Wenn Sie Methoden der `ThisDocument`-Klasse aufrufen, befolgen Sie diese Richtlinien:  
  
-   Den Standardwert eines optionalen akzeptieren **Ref** Parameter, übergeben Sie die `missing` -Variable an den Parameter. Die `missing`-Variable wird automatisch in Visual C# Office-Projekten definiert und dem <xref:System.Type.Missing>-Wert im generierten Projektcode zugewiesen.  
  
-   An Ihrem eigenen Wert für einen optionalen **Ref** Parameter, deklarieren Sie ein Objekt, das der Wert zugewiesen wird, die Sie angeben möchten, und klicken Sie dann das Objekt an den Parameter übergeben.  
  
 Im folgenden Codebeispiel wird veranschaulicht, wie zum Aufrufen der <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> Methode durch Angabe eines Werts für die *IgnoreUppercase* Parameter und der Standardwert für die anderen Parameter akzeptiert.  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]  
  
 Wenn Code schreiben, der optionale ausgelassen werden sollen **Ref** Parameter einer Methode in der `ThisDocument` -Klasse, können Sie alternativ die gleiche Methode auf Aufrufen der <xref:Microsoft.Office.Interop.Word.Document> zurückgegebenes Objekt die <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> -Eigenschaft, und lassen Sie die die Parameter in dieser Methode. Dies ist möglich, da <xref:Microsoft.Office.Interop.Word.Document> eine Schnittstelle und keine Klasse ist.  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]  
  
 Weitere Informationen zu Wert- und referenztypparametern finden Sie unter [übergeben von Argumenten als Wert und als Referenz &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (für Visual Basic) und [übergeben von Parametern &#40; C &#35; Programmierhandbuch &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Schreiben von Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)  
  
  