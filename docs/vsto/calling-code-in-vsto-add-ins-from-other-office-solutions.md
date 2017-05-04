---
title: "Aufrufen von Code in VSTO-Add-Ins aus anderen Office-Projektmappen | Microsoft Docs"
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
  - "VBA [Office-Entwicklung in Visual Studio], Aufrufen von Code in Add-Ins auf Anwendungsebene"
  - "Add-Ins auf Anwendungsebene [Office-Entwicklung in Visual Studio], Aufrufen von Code aus anderen Projektmappen"
  - "Aufrufen von Add-In-Code"
  - "Add-Ins [Office-Entwicklung in Visual Studio], Aufrufen von Code aus anderen Projektmappen"
  - "Interoperabilität [Office-Entwicklung in Visual Studio]"
  - "Aufrufen von Code aus VBA"
ms.assetid: c1f16b4c-9291-49ed-9694-a83a37109612
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Aufrufen von Code in VSTO-Add-Ins aus anderen Office-Projektmappen
  Sie können ein Objekt in Ihrem VSTO\-Add\-In für andere Projektmappen, einschließlich anderer Microsoft Office\-Projektmappen, verfügbar machen. Dies ist hilfreich, wenn Ihr VSTO\-Add\-In einen Dienst bereitstellt, der durch andere Projektmappen verwendet werden soll. Wenn Sie beispielsweise über ein VSTO\-Add\-In für Microsoft Office Excel verfügen, das Berechnungen in Bezug auf finanzielle Daten von einem Webdienst vornimmt, können andere Projektmappen diese Berechnungen ausführen, indem sie ein VSTO\-Add\-In für Excel zur Laufzeit aufrufen.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 In diesem Prozess gibt es zwei Hauptschritte:  
  
-   Machen Sie in Ihrem VSTO\-Add\-In ein Objekt für andere Projektmappen verfügbar.  
  
-   Greifen Sie in einer anderen Projektmappe auf das durch Ihr VSTO\-Add\-In verfügbar gemachtes Objekt zu, und rufen Sie Member des Objekts auf.  
  
## Lösungstypen, die Code in einem Add\-In aufrufen können  
 Sie können ein Objekt in einem VSTO\-Add\-In für die folgenden Projektmappentypen verfügbar machen:  
  
-   Visual Basic for Applications\-Code \(VBA\) in einem Dokument, das in demselben Anwendungsprozess wie Ihr VSTO\-Add\-In geladen wird.  
  
-   Anpassungen auf Dokumentebene, die in demselben Anwendungsprozess wie Ihr VSTO\-Add\-In geladen werden.  
  
-   Andere mithilfe der Office\-Projektvorlagen in Visual Studio erstellten VSTO\-Add\-In.  
  
-   COM\-VSTO\-Add\-Ins \(d. h. VSTO\-Add\-Ins, die die <xref:Extensibility.IDTExtensibility2>\-Schnittstelle direkt implementieren\).  
  
-   Eine beliebige Projektmappe, die in einem von Ihrem VSTO\-Add\-In unterschiedlichen Prozess ausgeführt wird \(diese Projektmappentypen werden auch als *prozessexterne Clients* bezeichnet\). Dazu zählen Anwendungen, die eine Office\-Anwendung automatisieren, beispielsweise eine Windows Forms\- oder Konsolenanwendung, sowie VSTO\-Add\-Ins, die in einem unterschiedlichen Prozess geladen sind.  
  
## Verfügbarmachen von Objekten für andere Lösungen  
 Führen Sie die folgenden Schritte in Ihrem VSTO\-Add\-In aus, um ein Objekt in Ihrem VSTO\-Add\-In für andere Projektmappen verfügbar zu machen:  
  
1.  Definieren Sie eine Klasse, die Sie für andere Lösungen verfügbar machen möchten.  
  
2.  Überschreiben Sie die <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>\-Methode in der `ThisAddIn`\-Klasse. Geben Sie eine Instanz der Klasse zurück, die Sie für andere Lösungen verfügbar machen möchten.  
  
### Definieren der für andere Lösungen verfügbar machenden Klasse  
 Die verfügbar machende Klasse muss mindestens auf öffentlich festgelegt werden, wobei das Attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> auf **true** festgelegt sein muss, und sie muss die Schnittstelle [IDispatch](http://msdn.microsoft.com/de-de/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) verfügbar machen.  
  
 Sie sollten die [IDispatch](http://msdn.microsoft.com/de-de/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)\-Schnittstelle mithilfe der folgenden Schritte verfügbar machen:  
  
1.  Definieren Sie eine Schnittstelle, die die Member deklariert, die Sie für andere Lösungen verfügbar machen möchten. Sie können diese Schnittstelle in Ihrem VSTO\-Add\-In\-Projekt definieren. Sie möchten diese Schnittstelle möglicherweise jedoch in einem separaten Klassenbibliotheksprojekt definieren, wenn Sie die Klasse für VBA\-fremde Projektmappen verfügbar machen möchten, sodass die Projektmappen, die Ihr VSTO\-Add\-In aufrufen, die Schnittstelle referenzieren können, ohne auf Ihr VSTO\-Add\-In\-Projekt zu verweisen.  
  
2.  Wenden Sie das Attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> auf diese Schnittstelle an, und legen Sie dieses Attribut auf **true** fest.  
  
3.  Ändern Sie Ihre Klasse zum Implementieren dieser Schnittstelle.  
  
4.  Wenden Sie das Attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> auf Ihre Klasse an, und legen Sie dieses Attribut auf den None\-Wert der <xref:System.Runtime.InteropServices.ClassInterfaceType>\-Aufzählung fest.  
  
5.  Wenn Sie die Klasse für prozessexterne Clients verfügbar machen möchten, müssen Sie möglicherweise Folgendes vornehmen:  
  
    -   Leiten Sie Klasse aus <xref:System.Runtime.InteropServices.StandardOleMarshalObject> ab. Weitere Informationen finden Sie unter [Verfügbarmachen von Klassen für prozessexterne Clients](#outofproc).  
  
    -   Legen Sie die Eigenschaft **Für COM\-Interop registrieren** im Projekt fest, in dem Sie die Schnittstelle definieren. Dies ist nur dann erforderlich, wenn Clients in der Lage sein sollen, die frühe Bindung zu verwenden, um einen Aufruf in das VSTO\-Add\-In vorzunehmen.  
  
 Das folgende Codebeispiel veranschaulicht eine `AddInUtilities`\-Klasse mit einer `ImportData`\-Methode, die durch andere Lösungen aufgerufen werden kann. Damit Sie diesen Code im Kontext oder eine umfangreichere exemplarische Vorgehensweise sehen können, lesen Sie bitte [Exemplarische Vorgehensweise: Aufrufen von Code aus VBA in einem VSTO-Add-In](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/AddInUtilities.cs#3)]
 [!code-vb[Trin_AddInInteropWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/AddInUtilities.vb#3)]  
  
### Verfügbarmachen von Klassen für VBA  
 Wenn Sie die oben aufgeführten Schritte ausführen, kann der VBA\-Code nur die Methoden aufrufen, die Sie in der Schnittstelle deklarieren. Der VBA\-Code kann keine anderen Methoden in Ihrer Klasse aufrufen, einschließlich der Methoden, die Ihre Klasse aus Basisklassen wie <xref:System.Object> abruft.  
  
 Sie können alternativ die Schnittstelle [IDispatch](http://msdn.microsoft.com/de-de/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) verfügbar machen, indem Sie das Attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> auf den Wert AutoDispatch oder AutoDual der <xref:System.Runtime.InteropServices.ClassInterfaceType>\-Aufzählung festlegen. Wenn Sie dies vornehmen, müssen Sie nicht die Methoden in einer separaten Schnittstelle deklarieren. Der VBA\-Code kann jedoch öffentliche und nicht statische Methoden in Ihrer Klasse aufrufen, einschließlich der Methoden, die aus Basisklassen wie <xref:System.Object> abgerufen wurden. Zudem können prozessexterne Clients, die die frühe Bindung verwenden, Ihre Klasse nicht aufrufen.  
  
###  <a name="outofproc"></a> Verfügbarmachen von Klassen für prozessexterne Clients  
 Wenn Sie eine Klasse in Ihrem VSTO\-Add\-In für prozessexterne Clients verfügbar machen möchten, sollten Sie die Klasse aus <xref:System.Runtime.InteropServices.StandardOleMarshalObject> ableiten, um sicherzustellen, dass prozessexterne Clients Ihr verfügbar gemachtes VSTO\-Add\-In\-Objekt aufrufen können. Ansonsten treten bei Versuchen, eine Instanz Ihres verfügbar gemachten Objekts in einem prozessexternen Client abzurufen, unerwartete Fehler auf.  
  
 Dies liegt daran, weil alle Aufrufe im Objektmodell einer Office\-Anwendung auf dem Hauptbenutzeroberflächen\-Thread vorgenommen werden müssen. Aufrufe vom prozessexternen Client für Ihr Objekt kommen jedoch auf einem willkürlichen Remoteprozeduraufruf\-Thread \(Remote Procedure Call, RPC\) an. Der COM\-Marshaling\-Mechanismus in .NET Framework wechselt die Threads nicht. Vielmehr versucht er, den Aufruf für Ihr Objekt auf dem eingehenden RPC\-Thread und nicht auf dem Hauptbenutzeroberflächen\-Thread zu marshallen. Wenn Ihr Objekt eine Instanz einer Klasse ist, die von <xref:System.Runtime.InteropServices.StandardOleMarshalObject> abstammt, werden eingehende Aufrufe für Ihr Objekt automatisch zum Thread gemarshallt, auf dem das verfügbar gemachte Objekt erstellt wurde, welcher demnach der Hauptbenutzeroberflächen\-Thread der Hostanwendung ist.  
  
 Weitere Informationen über das Verwenden von Threads in Office\-Projektmappen finden Sie unter [Threading-Unterstützung in Office](../vsto/threading-support-in-office.md).  
  
### Überschreiben der Methode "RequestComAddInAutomationService"  
 Das folgende Codebeispiel veranschaulicht, wie <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> in der `ThisAddIn`\-Klasse in Ihrem VSTO\-Add\-In überschrieben wird. In diesem Beispiel wird davon ausgegangen, dass Sie eine Klasse mit dem Namen `AddInUtilities` definiert haben, die Sie für andere Lösungen verfügbar machen möchten. Damit Sie diesen Code im Kontext oder eine umfangreichere exemplarische Vorgehensweise sehen können, lesen Sie bitte [Exemplarische Vorgehensweise: Aufrufen von Code aus VBA in einem VSTO-Add-In](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/ThisAddIn.vb#1)]  
  
 Wenn Ihr VSTO\-Add\-In geladen ist, ruft die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] die <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>\-Methode auf. Die Laufzeit weist das zurückgegebene Objekt der <xref:Microsoft.Office.Core.COMAddIn.Object%2A>\-Eigenschaft eines <xref:Microsoft.Office.Core.COMAddIn>\-Objekts zu, das Ihr VSTO\-Add\-In repräsentiert. Dieses <xref:Microsoft.Office.Core.COMAddIn>\-Objektsd ist für andere Office\-Lösungen verfügbar und für Lösungen, die Office automatisieren.  
  
## Zugreifen auf Objekte über andere Lösungen  
 Befolgen Sie zum Aufrufen des verfügbar gemachten Objekts in Ihrem VSTO\-Add\-In die folgenden Schritte in der Clientlösung:  
  
1.  Rufen Sie das <xref:Microsoft.Office.Core.COMAddIn>\-Objekt ab, das für das verfügbar gemachte VSTO\-Add\-In steht. Clients können mithilfe der Application.COMAddIns\-Eigenschaft im Objektmodell der Office\-Hostanwendung auf alle verfügbaren VSTO\-Add\-Ins zugreifen.  
  
2.  Greifen Sie auf die <xref:Microsoft.Office.Core.COMAddIn.Object%2A>\-Eigenschaft des <xref:Microsoft.Office.Core.COMAddIn>\-Objekts zu. Diese Eigenschaft gibt das verfügbar gemachte Objekt aus dem VSTO\-Add\-In zurück.  
  
3.  Rufen Sie die Member des verfügbar gemachten Objekts auf.  
  
 Die Art, wie Sie den Rückgabewert der Eigenschaft <xref:Microsoft.Office.Core.COMAddIn.Object%2A> verwenden, unterscheidet sich zwischen VBA\-Clients und Nicht\-VBA\-Clients. Für prozessexterne Clients ist zusätzlicher Code erforderlich, um eine mögliche Racebedingung zu vermeiden.  
  
### Zugreifen auf Objekte über VBA\-Lösungen  
 Das folgende Codebeispiel veranschaulicht, wie VBA zum Aufrufen einer Methode verwendet wird, die durch ein VSTO\-Add\-In verfügbar gemacht wird. Dieses VBA\-Makro ruft eine Methode mit dem Namen `ImportData` auf, die in einem VSTO\-Add\-In mit der Bezeichnung **ExcelImportData** definiert ist. Damit Sie diesen Code im Kontext oder eine umfangreichere exemplarische Vorgehensweise sehen können, lesen Sie bitte [Exemplarische Vorgehensweise: Aufrufen von Code aus VBA in einem VSTO-Add-In](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
```  
Sub CallVSTOMethod() Dim addIn As COMAddIn Dim automationObject As Object Set addIn = Application.COMAddIns("ExcelImportData") Set automationObject = addIn.Object automationObject.ImportData End Sub  
```  
  
### Zugreifen auf Objekte über Nicht\-VBA\-Lösungen  
 In einer Nicht\-VBA\-Lösung müssen Sie den <xref:Microsoft.Office.Core.COMAddIn.Object%2A>\-Eigenschaftswert zur Schnittstelle umwandeln, die er implementiert. Anschließend können Sie die verfügbar gemachten Methoden auf dem Schnittstellenobjekt aufrufen. Das folgende Codebeispiel veranschaulicht, wie die `ImportData`\-Methode von einem anderen VSTO\-Add\-In aufgerufen wird, das mit den Office Developer Tools in Visual Studio erstellt wurde.  
  
```vb  
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData") Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _ addIn.Object, ExcelImportData.IAddInUtilities) utilities.ImportData()  
```  
  
```csharp  
object addInName = "ExcelImportData"; Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName); ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object; utilities.ImportData();  
```  
  
 In diesem Beispiel gibt der Code eine <xref:System.InvalidCastException> zurück, wenn Sie versuchen, den Wert der Eigenschaft <xref:Microsoft.Office.Core.COMAddIn.Object%2A> zur Klasse `AddInUtilities` und nicht zur `IAddInUtilities`\-Schnittstelle umzuwandeln.  
  
## Siehe auch  
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Exemplarische Vorgehensweise: Aufrufen von Code aus VBA in einem VSTO-Add-In](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Anpassen von Features der Benutzeroberfläche mithilfe von Erweiterungsschnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  