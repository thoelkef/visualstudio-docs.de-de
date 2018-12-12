---
title: Aufrufen von Code in VSTO-Add-ins aus anderen Office-Projektmappen
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9290fcdd705f6f38b4b7e91e46d5b635f1e309ff
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248097"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Aufrufen von Code in VSTO-Add-ins aus anderen Office-Projektmappen
  Sie können ein Objekt in Ihrem VSTO-Add-In für andere Projektmappen, einschließlich anderer Microsoft Office-Projektmappen, verfügbar machen. Dies ist hilfreich, wenn Ihr VSTO-Add-In einen Dienst bereitstellt, der durch andere Projektmappen verwendet werden soll. Z. B. Wenn Sie ein VSTO-Add-in für Microsoft Office Excel, die Berechnungen auf finanzielle Daten von einem Webdienst vornimmt verfügen, können andere Projektmappen diese Berechnungen durch den Aufruf in das Excel-VSTO-Add-in zur Laufzeit ausführen.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 In diesem Prozess gibt es zwei Hauptschritte:  
  
-   Machen Sie in Ihrem VSTO-Add-In ein Objekt für andere Projektmappen verfügbar.  
  
-   Greifen Sie in einer anderen Projektmappe auf das durch Ihr VSTO-Add-In verfügbar gemachtes Objekt zu, und rufen Sie Member des Objekts auf.  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Arten von Lösungen, die in einem Add-in-Code aufgerufen werden kann  
 Sie können ein Objekt in einem VSTO-Add-in der folgenden Typen von Projektmappen verfügbar machen:  
  
-   Visual Basic for Applications-Code (VBA) in einem Dokument, das in demselben Anwendungsprozess wie Ihr VSTO-Add-In geladen wird.  
  
-   Anpassungen auf Dokumentebene, die in demselben Anwendungsprozess wie Ihr VSTO-Add-In geladen werden.  
  
-   Andere mithilfe der Office-Projektvorlagen in Visual Studio erstellten VSTO-Add-In.  
  
-   COM-VSTO-Add-Ins (d. h. VSTO-Add-Ins, die die <xref:Extensibility.IDTExtensibility2> -Schnittstelle direkt implementieren).  
  
-   Eine beliebige Projektmappe, die in einem von Ihrem VSTO-Add-In unterschiedlichen Prozess ausgeführt wird (diese Projektmappentypen werden auch als *prozessexterne Clients*bezeichnet). Dazu zählen Anwendungen, die eine Office-Anwendung automatisieren, beispielsweise eine Windows Forms- oder Konsolenanwendung, sowie VSTO-Add-Ins, die in einem unterschiedlichen Prozess geladen sind.  
  
## <a name="expose-objects-to-other-solutions"></a>Machen Sie Objekte für andere Projektmappen verfügbar  
 Führen Sie die folgenden Schritte in Ihrem VSTO-Add-In aus, um ein Objekt in Ihrem VSTO-Add-In für andere Projektmappen verfügbar zu machen:  
  
1.  Definieren Sie eine Klasse, die Sie für andere Lösungen verfügbar machen möchten.  
  
2.  Überschreiben Sie die <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> -Methode in der `ThisAddIn` -Klasse. Geben Sie eine Instanz der Klasse zurück, die Sie für andere Lösungen verfügbar machen möchten.  
  
### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Definieren Sie die Klasse, die Sie für andere Lösungen verfügbar machen möchten.  
 Die verfügbar machende Klasse muss mindestens auf öffentlich festgelegt werden, wobei das Attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> auf **true**festgelegt sein muss, und sie muss die Schnittstelle [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) verfügbar machen.  
  
 Sie sollten die [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) -Schnittstelle mithilfe der folgenden Schritte verfügbar machen:  
  
1. Definieren Sie eine Schnittstelle, die die Member deklariert, die Sie für andere Lösungen verfügbar machen möchten. Sie können diese Schnittstelle in Ihrem VSTO-Add-In-Projekt definieren. Sie möchten diese Schnittstelle möglicherweise jedoch in einem separaten Klassenbibliotheksprojekt definieren, wenn Sie die Klasse für VBA-fremde Projektmappen verfügbar machen möchten, sodass die Projektmappen, die Ihr VSTO-Add-In aufrufen, die Schnittstelle referenzieren können, ohne auf Ihr VSTO-Add-In-Projekt zu verweisen.  
  
2. Wenden Sie das Attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> auf diese Schnittstelle an, und legen Sie dieses Attribut auf **true**fest.  
  
3. Ändern Sie Ihre Klasse zum Implementieren dieser Schnittstelle.  
  
4. Anwenden der <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> -Attribut auf die Klasse, und legen Sie dieses Attribut auf die **keine** Wert, der die <xref:System.Runtime.InteropServices.ClassInterfaceType> Enumeration.  
  
5. Wenn Sie dieser Klasse, die Out-of-Process-Clients verfügbar machen möchten, müssen Sie möglicherweise auch die folgenden Schritte ausführen:  
  
   -   Leiten Sie Klasse aus <xref:System.Runtime.InteropServices.StandardOleMarshalObject>ab. Weitere Informationen finden Sie unter [Klassen Out-of-Process-Clients verfügbar macht](#outofproc).  
  
   -   Legen Sie die Eigenschaft **Für COM-Interop registrieren** im Projekt fest, in dem Sie die Schnittstelle definieren. Diese Eigenschaft ist nur erforderlich, wenn Sie Clients, die frühen Bindung zu verwenden, um das VSTO-Add-in Aufrufen von aktivieren möchten.  
  
   Das folgende Codebeispiel veranschaulicht eine `AddInUtilities` -Klasse mit einer `ImportData` -Methode, die durch andere Lösungen aufgerufen werden kann. Dieser Code im Kontext einer größeren exemplarischen Vorgehensweise finden Sie unter [Exemplarische Vorgehensweise: Aufrufen von Code in einem VSTO-Add-in aus VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
   [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
   [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="expose-classes-to-vba"></a>Klassen für VBA verfügbar macht  
 Wenn Sie die oben aufgeführten Schritte ausführen, kann der VBA-Code nur die Methoden aufrufen, die Sie in der Schnittstelle deklarieren. Der VBA-Code kann keine anderen Methoden in Ihrer Klasse aufrufen, einschließlich der Methoden, die Ihre Klasse aus Basisklassen wie <xref:System.Object>abruft.  
  
 Sie können alternativ verfügbar machen die [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) Schnittstelle durch Festlegen der <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> -Attributs auf den AutoDispatch oder AutoDual-Wert, der der <xref:System.Runtime.InteropServices.ClassInterfaceType> Enumeration. Wenn Sie die Schnittstelle verfügbar machen, müssen Sie nicht die Methoden in einer separaten Schnittstelle deklarieren. Der VBA-Code kann jedoch öffentliche und nicht statische Methoden in Ihrer Klasse aufrufen, einschließlich der Methoden, die aus Basisklassen wie <xref:System.Object>abgerufen wurden. Zudem können prozessexterne Clients, die die frühe Bindung verwenden, Ihre Klasse nicht aufrufen.  
  
###  <a name="outofproc"></a> Klassen für Out-of-Process-Clients verfügbar macht  
 Wenn Sie eine Klasse in Ihrem VSTO-Add-In für prozessexterne Clients verfügbar machen möchten, sollten Sie die Klasse aus <xref:System.Runtime.InteropServices.StandardOleMarshalObject> ableiten, um sicherzustellen, dass prozessexterne Clients Ihr verfügbar gemachtes VSTO-Add-In-Objekt aufrufen können. Ansonsten treten bei Versuchen, eine Instanz Ihres verfügbar gemachten Objekts in einem prozessexternen Client abzurufen, unerwartete Fehler auf.  
  
 Dieser Fehler ist, da alle Aufrufe an das Objektmodell einer Office-Anwendung müssen auf dem Hauptbenutzeroberflächen-Thread erfolgen, aber die Aufrufe von einem Out-of-Process-Client für Ihr Objekt auf einen beliebigen Thread der RPC (Remoteprozeduraufrufe) gelangen. Der COM-Marshaling-Mechanismus in .NET Framework wechselt die Threads nicht. Vielmehr versucht er, den Aufruf für Ihr Objekt auf dem eingehenden RPC-Thread und nicht auf dem Hauptbenutzeroberflächen-Thread zu marshallen. Wenn Ihr Objekt eine Instanz einer Klasse ist, die von <xref:System.Runtime.InteropServices.StandardOleMarshalObject>abstammt, werden eingehende Aufrufe für Ihr Objekt automatisch zum Thread gemarshallt, auf dem das verfügbar gemachte Objekt erstellt wurde, welcher demnach der Hauptbenutzeroberflächen-Thread der Hostanwendung ist.  
  
 Weitere Informationen zur Verwendung von Threads in Office-Projektmappen finden Sie unter [Threading-Unterstützung in Office](../vsto/threading-support-in-office.md).  
  
### <a name="override-the-requestcomaddinautomationservice-method"></a>Überschreiben Sie die Methode "RequestComAddInAutomationService"  
 Das folgende Codebeispiel veranschaulicht, wie <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> in der `ThisAddIn` -Klasse in Ihrem VSTO-Add-In überschrieben wird. Im Beispiel wird davon ausgegangen, dass Sie eine Klasse namens definiert haben `AddInUtilities` , die Sie für andere Projektmappen verfügbar machen möchten. Dieser Code im Kontext einer größeren exemplarischen Vorgehensweise finden Sie unter [Exemplarische Vorgehensweise: Aufrufen von Code in einem VSTO-Add-in aus VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 Wenn Ihr VSTO-Add-In geladen ist, ruft die [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] die <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> -Methode auf. Die Laufzeit weist das zurückgegebene Objekt der Eigenschaft COMAddIn.Object eine <xref:Microsoft.Office.Core.COMAddIn> Objekt, das Ihr VSTO-Add-in darstellt. Dieses <xref:Microsoft.Office.Core.COMAddIn> -Objektsd ist für andere Office-Lösungen verfügbar und für Lösungen, die Office automatisieren.  
  
## <a name="access-objects-from-other-solutions"></a>Zugreifen auf Objekte aus anderen Projektmappen  
 Befolgen Sie zum Aufrufen des verfügbar gemachten Objekts in Ihrem VSTO-Add-In die folgenden Schritte in der Clientlösung:  
  
1. Rufen Sie das <xref:Microsoft.Office.Core.COMAddIn>-Objekt ab, das für das verfügbar gemachte VSTO-Add-In steht. Clients können mithilfe der `Application.COMAddIns`-Eigenschaft im Objektmodell der Office-Hostanwendung auf alle verfügbaren VSTO-Add-Ins zugreifen.  
  
2. Zugriff auf die COMAddIn.Object-Eigenschaft, der die <xref:Microsoft.Office.Core.COMAddIn> Objekt. Diese Eigenschaft gibt das verfügbar gemachte Objekt aus dem VSTO-Add-In zurück.  
  
3. Rufen Sie die Member des verfügbar gemachten Objekts auf.  
  
   Die Möglichkeit, dass Sie den Rückgabewert der Eigenschaft COMAddIn.Object verwenden, ist für VBA-Clients und nicht-VBA-Clients unterschiedlich. Für prozessexterne Clients ist zusätzlicher Code erforderlich, um eine mögliche Racebedingung zu vermeiden.  
  
### <a name="access-objects-from-vba-solutions"></a>Zugreifen auf Objekte über VBA-Lösungen  
 Im folgenden Codebeispiel wird veranschaulicht, wie VBA verwendet, um eine Methode aufzurufen, die von einem VSTO-Add-in verfügbar gemacht wird. Dieses VBA-Makro ruft eine Methode namens `ImportData` in einem VSTO-Add-in mit dem Namen definierten **ExcelImportData**. Dieser Code im Kontext einer größeren exemplarischen Vorgehensweise finden Sie unter [Exemplarische Vorgehensweise: Aufrufen von Code in einem VSTO-Add-in aus VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
```vb
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="access-objects-from-non-vba-solutions"></a>Zugreifen auf Objekte von nicht-VBA-Projektmappen  
 Klicken Sie in einer nicht-VBA-Projektmappe müssen Sie den Wert der COMAddIn.Object-Eigenschaften, die die implementierte Schnittstelle umwandeln, und anschließend können Sie die verfügbar gemachten Methoden auf dem Schnittstellenobjekt aufrufen. Das folgende Codebeispiel veranschaulicht, wie die `ImportData` -Methode von einem anderen VSTO-Add-In aufgerufen wird, das mit den Office Developer Tools in Visual Studio erstellt wurde.  
  
```vb  
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")  
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _  
    addIn.Object, ExcelImportData.IAddInUtilities)  
utilities.ImportData()  
```  
  
```csharp  
object addInName = "ExcelImportData";  
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);  
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;  
utilities.ImportData();  
```  
  
 In diesem Beispiel, wenn Sie versuchen, den Wert der Eigenschaft COMAddIn.Object Umwandeln der `AddInUtilities` Klasse anstelle der `IAddInUtilities` -Schnittstelle, der Code löst eine <xref:System.InvalidCastException>.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Exemplarische Vorgehensweise: Aufrufen von Code in einem VSTO-Add-in aus VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)   
 [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Anpassen von Funktionen der Benutzeroberfläche mithilfe von Erweiterbarkeitsschnittstellen](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  
