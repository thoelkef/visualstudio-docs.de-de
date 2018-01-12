---
title: Schreiben von Code in Office-Projektmappen | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e9670bb35023b2a2cf4147d3d30008243203c9c8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="writing-code-in-office-solutions"></a>Schreiben von Code in Office-Projektmappen
  Einige Aspekte beim Schreiben von Code in Office-Projekten unterscheiden sich von anderen Projekttypen. Viele dieser Unterscheide haben mit der Art zu tun, wie die Office-Objektmodelle im verwalteten Code verfügbar gemacht werden. Andere Unterschiede beziehen sich auf den Entwurf von Office-Projekten.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="managed-code-and-office-programming"></a>Verwalteter Code und Office-Programmierung  
 Die Schlüsseltechnologie, die das Erstellen integrierter Microsoft Office-Projektmappen ermöglicht, ist die Automatisierung. Automatisierung ist Teil der COM-Technologie (Component Object Model). Automatisierung ermöglicht Ihnen die Verwendung von Code zum Erstellen und Steuern von Softwareobjekten, die von einer Anwendung, einer DLL oder einem ActiveX-Steuerelement verfügbar gemacht wird, die bzw. das die entsprechende Programmierschnittstelle unterstützt.  
  
### <a name="understanding-primary-interop-assemblies"></a>Grundlegendes zu primären Interopassemblys  
 Viele Funktionen der Microsoft Office-Anwendungen sind für die Automatisierung zugänglich. Sie können verwalteten Code (z. B. Visual Basic oder C#) jedoch nicht direkt zum Automatisieren von Office-Anwendungen verwenden. Zum Automatisieren von Office-Anwendungen mithilfe von verwaltetem Code müssen die primären Office-Interopassemblys verwendet werden. Mithilfe der primären Interopassemblys kann verwalteter Code mit dem COM-basierten Objektmodell der Office-Anwendungen interagieren.  
  
 Jede Microsoft Office-Anwendung verfügt über eine primäre Interopassembly (PIA). Wenn Sie in Visual Studio ein Office-Projekt erstellen, wird dem Projekt automatisch ein Verweis auf die entsprechende PIA hinzugefügt. Zum Automatisieren der Funktionen anderer Office-Anwendungen aus dem Projekt muss der entsprechenden primären Interopassembly (PIA) manuell ein Verweis hinzugefügt werden. Weitere Informationen finden Sie unter [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
### <a name="using-primary-interop-assemblies-at-design-time-and-run-time"></a>Verwenden von primären Interopassemblys zur Entwurfs- und Laufzeit  
 Die Office-PIAs müssen im globalen Assemblycache auf dem Entwicklungscomputer installiert und registriert sein, damit Sie die meisten Entwicklungsaufgaben ausführen können. Weitere Informationen finden Sie unter [Configuring a Computer to Develop Office Solutions](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 Die Office-PIAs sind jedoch auf Endbenutzercomputern nicht erforderlich, um Office-Projektmappen auszuführen, für die als Zielversion [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder höher festgelegt wurde. Weitere Informationen finden Sie unter [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="using-types-in-primary-interop-assemblies"></a>Verwenden von Typen in primären Interopassemblys  
 Die Office-PIAs enthalten eine Kombination von Typen, die das Objektmodell der Office-Anwendungen und zusätzliche Infrastrukturtypen verfügbar machen, die nicht zur direkten Verwendung im Code vorgesehen sind. Eine Übersicht über die Typen in den Office-PIAs finden Sie unter [Overview of Classes and Interfaces in the Office Primary Interop Assemblies](http://msdn.microsoft.com/en-us/da92dc3c-8209-44de-8095-a843659368d5).  
  
 Da die Typen in den Office-PIAs Typen in den COM-basierten Objektmodellen entsprechen, unterscheidet sich die Art der Verwendung dieser Typen von der anderer verwalteter Typen. Zum Beispiel hängt die Art, wie Sie Methoden mit optionalen Parameter in einer primären Interopassembly von Office aufrufen, von der im Projekt verwendeten Programmiersprache ab. Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md).  
  
-   [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md).  
  
## <a name="programming-model-of-office-projects"></a>Programmiermodell von Office-Projekten  
 Alle Office-Projekte schließen mindestens eine generierte Klasse ein, die den Einstiegspunkt für den Code darstellt. Diese Klassen bieten auch Zugriff auf das Objektmodell der Hostanwendung und Zugriff auf Funktionen wie Aktionsbereiche und benutzerdefinierte Aufgabenbereiche.  
  
### <a name="understanding-the-generated-classes"></a>Grundlegendes zu den generierten Klassen  
 In Projekten auf Dokumentebene für Excel und Word ähnelt die generierte Klasse einem Objekt der obersten Ebene im Objektmodell der Anwendung. Die generierte `ThisDocument` -Klasse in einem Word-Dokumentprojekt stellt beispielsweise dieselben Member wie die <xref:Microsoft.Office.Interop.Word.Document> -Klasse im Word-Objektmodell bereit. Weitere Informationen zu den generierten Klassen in Projekten auf Dokumentebene finden Sie unter [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md).  
  
 In VSTO-Add-In-Projekten wird eine generierte Klasse namens `ThisAddIn`bereitgestellt. Diese Klasse ähnelt keiner Klasse im Objektmodell der Hostanwendung. Diese Klasse stellt stattdessen das VSTO-Add-In selbst dar und stellt Member bereit, mit denen Sie auf das Objektmodell der Hostanwendung und auf andere Funktionen zugreifen können, die für VSTO-Add-Ins verfügbar sind. Weitere Informationen finden Sie unter [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Alle generierten Klassen in Office-Projekte enthalten die Ereignishandler `Startup` und `Shutdown` . In der Regel wird diesen Ereignishandlern Code hinzugefügt, um mit dem Schreiben von Code zu beginnen. Um das VSTO-Add-In zu initialisieren, können Sie dem `Startup` -Ereignishandler Code hinzufügen. Um vom VSTO-Add-In verwendete Ressourcen zu bereinigen, können Sie dem `Shutdown` -Ereignishandler Code hinzufügen. Weitere Informationen finden Sie unter [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
### <a name="accessing-the-generated-classes-at-run-time"></a>Zugreifen auf die generierten Klassen zur Laufzeit  
 Wenn eine Office-Lösung geladen wird, wird jede generierte Klasse im Projekt von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instanziiert. Sie können auf diese Objekte von einem beliebigen Code im Projekt mithilfe der `Globals` -Klasse zugreifen. Sie können zum Beispiel mit der `Globals` -Klasse Code in der `ThisAddIn` -Klasse aus einem Ereignishandler einer Menübandschaltfläche in einem VSTO-Add-In aufrufen.  
  
 Weitere Informationen finden Sie unter [globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="namespace-considerations-in-office-solutions"></a>Überlegungen zu Namespaces in Office-Projektmappen  
 Der *Standardnamespace* (oder *Stammnamespace* in Visual Basic) eines Office-Projekts kann nach dem Erstellen des Projekts nicht mehr geändert werden. Der Standardnamespace entspricht immer dem Projektnamen, den Sie beim Erstellen des Projekts angegeben haben. Wenn Sie das Projekt umbenennen, ändert sich der Standardnamespace nicht. Weitere Informationen zum Standardnamespace in Projekten finden Sie unter [Anwendungsseite, Projekt-Designer &#40; C &#35; &#41; ](/visualstudio/ide/reference/application-page-project-designer-csharp) und [Anwendungsseite, Projekt-Designer &#40; Visual Basic &#41; ](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
### <a name="changing-the-namespace-of-host-item-classes-in-c-projects"></a>Ändern des Namespace von Hostelementklassen in C#-Projekten  
 Hostelementklassen (z. B. die `ThisAddIn`-, `ThisWorkbook`- oder `ThisDocument` -Klassen) verfügen über eigene Namespaces in Visual C#-Office-Projekten. Der Namespace für Hostelemente im Projekt entspricht standardmäßig dem Projektnamen, den Sie beim Erstellen des Projekts angegeben haben.  
  
 Verwenden Sie die Eigenschaft **Namespace für Hostelement** , um den Namespace der Hostelemente in einem Visual C#-Office-Projekt zu ändern. Weitere Informationen finden Sie unter [Eigenschaften in Office-Projekten](../vsto/properties-in-office-projects.md).  
  
## <a name="supported-programming-languages-in-office-projects"></a>Unterstützte Programmiersprachen in Office-Projekten  
 Die Office-Projektvorlagen in Visual Studio unterstützen nur die Programmiersprachen Visual Basic und Visual C#. Daher sind diese Projektvorlagen nur unter den Knoten **Visual Basic** und **Visual C#** des Dialogfelds **Neues Projekt** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]verfügbar. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="language-choice-and-office-programming"></a>Sprachauswahl und Office-Programmierung  
 Microsoft Office und Visual Basic for Applications (VBA) wurden so entwickelt, dass sie ineinander greifen, um den Workflow der Anwendungsanpassung zu optimieren. Visual Basic hat einige dieser Entwicklungen geerbt. Visual Basic unterstützt z. B. optionale Parameter, d. h. im Vergleich zu Visual C# können Sie beim Aufruf einiger Methoden in den primären Interopassemblys von Microsoft Office weniger Code schreiben.  
  
## <a name="programming-with-visual-basic-vs-visual-c-in-office-solutions"></a>Programmierung mit Visual Basic und mit Visual C# in Office-Projektmappen  
 Sie können Office-Lösungen entweder mit Visual Basic oder Visual C# erstellen. Da die Microsoft Office-Objektmodelle zur Verwendung mit Microsoft Visual Basic for Applications (VBA) entwickelt wurden, können Visual Basic-Entwickler problemlos mit den von den Microsoft Office-Anwendungen verfügbar gemachten Objekten arbeiten. Visual C#-Entwickler können größtenteils die gleichen Funktionen wie Visual Basic-Entwickler nutzen, aber in einigen Fällen müssen sie zusätzlichen Code verfassen, um die Office-Objektmodelle verwenden zu können. Es gibt auch einige Unterschiede zwischen den grundlegenden Programmierfunktionen für die Office-Entwicklung und in Visual Basic und C# geschriebenem verwalteten Code.  
  
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Wesentliche Unterschiede zwischen Visual Basic und Visual C#  
 In der folgenden Tabelle werden die wichtigsten Unterschiede zwischen Visual Basic und Visual C# bei der Office-Entwicklung angezeigt.  
  
|Funktion|Beschreibung|Visual Basic-Unterstützung|Visual C#-Unterstützung|  
|-------------|-----------------|--------------------------|------------------------|  
|Optionale Parameter|Viele Microsoft Office-Methoden verfügen über Parameter, die nicht erforderlich sind, wenn Sie die Methode aufrufen. Wenn kein Wert für den Parameter übergeben wird, wird ein Standardwert verwendet.|Visual Basic unterstützt optionale Parameter.|Visual C# unterstützt in den meisten Fällen optionale Parameter. Weitere Informationen finden Sie unter [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md).|  
|Übergeben von Parametern durch einen Verweis|Optionale Parameter können in den meisten der primären Interopassemblys von Microsoft Office als Wert übergeben werden. In manchen primären Interopassemblys müssen optionale Parameter, die Referenztypen akzeptieren, jedoch als Verweis übergeben werden.<br /><br /> Weitere Informationen zu Wert- und referenztypparametern finden Sie unter [übergeben von Argumenten als Wert und als Referenz &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (für Visual Basic) und [übergeben von Parametern &#40; C &#35; Programmierhandbuch &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|Es sind keine weiteren Aufgaben erforderlich, um Parameter als Verweis zu übergeben. Der Visual Basic-Compiler übergibt die Parameter automatisch durch einen Verweis, wenn dies erforderlich ist.|In den meisten Fällen übergibt der Visual C#-Compiler automatisch die Parameter durch einen Verweis, wenn dies erforderlich ist. Weitere Informationen finden Sie unter [Optionaler Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md).|  
|Parametrisierte Eigenschaften|Einige Eigenschaften akzeptieren Parameter und fungieren als schreibgeschützte Funktionen.|Visual Basic unterstützt Eigenschaften, die Parameter akzeptieren.|Visual C# unterstützt Eigenschaften, die Parameter akzeptieren.|  
|Spätes Binden|Bei der späten Bindung werden die Eigenschaften von Objekten zur Laufzeit bestimmt, statt Variablen zur Entwurfszeit in den Objekttyp umzuwandeln.|Visual Basic führt späte Bindungen aus, wenn **Option Strict** deaktiviert ist. Wenn **Option Strict** aktiviert ist, müssen Objekte explizit konvertiert und Typen im <xref:System.Reflection> -Namespace verwendet werden, um auf spät gebundene Member zugreifen zu können. Weitere Informationen finden Sie unter [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md).|Visual C# führt späte Bindungen in Projekten aus, für die als Zielversion [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]festgelegt wurde. Weitere Informationen finden Sie unter [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md).|  
  
## <a name="key-differences-between-office-development-and-managed-code"></a>Hauptunterschiede zwischen Office-Entwicklung und verwaltetem Code  
 In der folgenden Tabelle werden die wichtigsten Unterschiede zwischen der Office-Entwicklung und verwaltetem Code angezeigt, der mit Visual Basic und Visual C# geschrieben wurde.  
  
|Funktion|Beschreibung|Visual Basic- und Visual C#-Unterstützung|  
|-------------|-----------------|-----------------------------------------|  
|Arrayindizes|Die unteren Arraygrenzen der Auflistungen in Microsoft Office-Anwendungen beginnen mit 1. Visual Basic und Visual C# verwenden 0-basierte Arrays. Weitere Informationen finden Sie unter [Arrays &#40; C &#35; Programmierhandbuch &#41; ](/dotnet/csharp/programming-guide/arrays/index) und [Arrays in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Um auf das erste Element einer Auflistung im Objektmodell einer Microsoft Office-Anwendung zuzugreifen, verwenden Sie den Index 1 statt 0.|  
  
## <a name="see-also"></a>Siehe auch  
 [Optionale Parameter in Office-Projektmappen](../vsto/optional-parameters-in-office-solutions.md)   
 [Globaler Zugriff auf Objekte in Office-Projekten](../vsto/global-access-to-objects-in-office-projects.md)   
 [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md)   
 [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Vorgehensweise: Erstellen von Ereignishandlern in Office-Projekten](../vsto/how-to-create-event-handlers-in-office-projects.md)   
 [Späte Bindung in Office-Projektmappen](../vsto/late-binding-in-office-solutions.md)   
 [Gemeinsame Entwicklung von Office-Projektmappen](../vsto/collaborative-development-of-office-solutions.md)  
  
  