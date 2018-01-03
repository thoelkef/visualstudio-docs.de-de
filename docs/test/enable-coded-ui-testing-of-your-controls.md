---
title: Aktivieren von Tests der programmierten UI Ihrer Steuerelemente | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: "22"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: d44026c2a4424cbacd16af57d3fb132d23ba8068
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Aktivieren von Tests der programmierten UI Ihrer Steuerelemente
Steuerelemente können einfacher getestet werden, wenn Sie Unterstützung für das Framework für den Test der programmierten UI implementieren. Der Umfang der Unterstützung kann schrittweise erweitert werden. Sie können zunächst mit der Unterstützung von Aufzeichnung und Wiedergabe sowie Eigenschaftenvalidierung beginnen. Darauf aufbauend können Sie dem Test-Generator für programmierte UI ermöglichen, die benutzerdefinierten Eigenschaften des Steuerelements zu erkennen, und benutzerdefinierte Klassen bereitstellen, um mit generiertem Code auf diese Eigenschaften zuzugreifen. Außerdem können Sie dazu beitragen, dass Aktionen vom Test-Generator der programmierten UI auf eine Art aufgezeichnet werden, die den Zweck der jeweiligen Aktion genauer widerspiegelt.  
  
 **In diesem Thema:**  
  
1.  [Datensatz-, Wiedergabe -und Eigenschaftvalidierung durch Implementierung der Barrierefreiheit unterstützen](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)  
  
2.  [Benutzerdefinierte Eigenschaftenvalidierung durch Implementierung eines Eigenschaftenanbieters unterstützen](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)  
  
3.  [Codegenerierung durch Implementierung einer Klasse zum Zugriff auf benutzerdefinierte Eigenschaften unterstützen](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)  
  
4.  [Absichtsbewusste Aktionen durch Implementierung eines Aktionsfilters unterstützen](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)  
  
 ![CUIT&#95;Full](../test/media/cuit_full.png "CUIT_Full")  
  
##  <a name="recordandplayback"></a> Datensatz-, Wiedergabe -und Eigenschaftvalidierung durch Implementierung der Barrierefreiheit unterstützen  
 Der Test-Generator der programmierten UI erfasst Informationen zu den Steuerelementen, die während einer Aufzeichnung gefunden werden, und generiert dann Code zur Wiedergabe dieser Sitzung. Wenn Barrierefreiheit vom Steuerelement nicht unterstützt wird, erfasst der Test-Generator für codierte UI Aktionen wie Mausklicks anhand der Bildschirmkoordinaten. Bei der Wiedergabe des Tests werden diese Mausklicks vom generierten Code an den gleichen Bildschirmkoordinaten ausgeführt. Wenn sich das Steuerelement beim Wiedergeben des Tests an einer anderen Stelle auf dem Bildschirm befindet, kann der generierte Code die entsprechende Aktion für das Steuerelement nicht ausführen. Dies kann zu Fehlern führen, wenn die Testwiedergabe auf unterschiedlichen Bildschirmkonfigurationen oder in anderen Umgebungen erfolgt oder Änderungen am Benutzeroberflächenlayout vorgenommen wurden.  
  
 ![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png "CUIT_RecordNoSupport")  
  
 Wenn Sie jedoch Barrierefreiheit implementieren, wird diese vom Test-Generator der programmierten UI im Rahmen der Testaufzeichnung und Codegenerierung für das Erfassen der Informationen zum Steuerelement verwendet. Bei der anschließenden Ausführung des Tests erfolgt die Wiedergabe der entsprechenden Ereignisse durch den generierten Code auf dem Steuerelement, auch wenn sich dieses an einer anderen Stelle der Benutzeroberfläche befindet. Testautors können mithilfe der grundlegenden Eigenschaften des Steuerelements auch Asserts erstellen.  
  
 ![CUIT&#95;Record](../test/media/cuit_record.png "CUIT_Record")  
  
### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>So unterstützen Sie Aufzeichnung und Wiedergabe, Eigenschaftvalidierung und Navigation für ein Windows Forms-Steuerelement  
 Barrierefreiheit kann wie in der folgenden Prozedur dargestellt implementieren werden. Ein ausführliche Anleitung finden Sie unter <xref:System.Windows.Forms.AccessibleObject>.  
  
 ![CUIT&#95;Accessible](../test/media/cuit_accessible.png "CUIT_Accessible")  
  
1.  Implementieren Sie eine von <xref:System.Windows.Forms.Control.ControlAccessibleObject> abgeleitete Klasse, und überschreiben Sie die <xref:System.Windows.Forms.Control.AccessibilityObject%2A>-Eigenschaft, um ein Objekt der Klasse zurückzugeben.  
  
    ```csharp  
    public partial class ChartControl : UserControl  
    {  
        // Overridden to return the custom AccessibleObject for the control.  
        protected override AccessibleObject CreateAccessibilityInstance()  
        {  
            return new ChartControlAccessibleObject(this);  
        }  
  
        // Inner class ChartControlAccessibleObject represents accessible information  
        // associated with the ChartControl and is used when recording tests.  
        public class ChartControlAccessibleObject : ControlAccessibleObject  
        {  
            ChartControl myControl;  
            public ChartControlAccessibleObject(ChartControl ctrl)  
                : base(ctrl)  
            {  
                myControl = ctrl;  
            }  
        }  
    }  
    ```  
  
2.  Überschreiben Sie die Eigenschaften und Methoden <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> sowie <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> des Barrierefreiheitsobjekts.  
  
3.  Implementieren Sie ein anderes Barrierefreiheitsobjekt für das untergeordnete Steuerelement, und überschreiben Sie die <xref:System.Windows.Forms.Control.AccessibilityObject%2A>-Eigenschaft dieses Steuerelements, um das Barrierefreiheitsobjekt zurückzugeben.  
  
4.  Überschreiben Sie die Eigenschaften und Methoden <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A> sowie <xref:System.Windows.Forms.AccessibleObject.Select%2A> für das Barrierefreiheitsobjekt des untergeordneten Steuerelements.  
  
> [!NOTE]
>  Dieses Thema beginnt mit dem Barrierefreiheitsbeispiel für das <xref:System.Windows.Forms.AccessibleObject> in dieser Prozedur. Darauf aufbauend werden anschließend die restlichen Prozeduren erläutert. Zum Erstellen einer funktionierenden Version des Barrierefreiheitsbeispiels entwickeln Sie eine Konsolenanwendung und ersetzen dann den Code in "Program.cs" durch den Beispielcode. Sie müssen Verweise auf Barrierefreiheit, System.Drawing und System.Windows.Forms hinzufügen. Sie sollten für die Barrierefreiheit **Interoptypen einbetten** zu **FALSE** ändern, um eine Buildwarnungen zu vermeiden. Sie können den Ausgabetyp des Projekts von **Konsolenanwendung** in **Windows-Anwendung** ändern, damit beim Ausführen der Anwendung kein Konsolenfenster angezeigt wird.  
  
##  <a name="customproprties"></a> Benutzerdefinierte Eigenschaftenvalidierung durch Implementierung eines Eigenschaftenanbieters unterstützen  
 Sobald Sie grundlegende Unterstützung für die Aufzeichnung und Wiedergabe sowie die Eigenschaftenvalidierung implementiert haben, können Sie die benutzerdefinierten Eigenschaften des Steuerelements für Tests der programmierten UI verfügbar machen, indem Sie ein <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>-Plug-In implementieren. Beispielsweise wird von der folgenden Prozedur ein Eigenschaftenanbieter erstellt, mit dem Tests der programmierten UI auf die Zustandseigenschaft der untergeordneten CurveLegend-Steuerelemente des Diagrammsteuerelements zugreifen können.  
  
 ![CUIT&#95;CustomProps](../test/media/cuit_customprops.png "CUIT_CustomProps")  
  
### <a name="to-support-custom-property-validation"></a>So unterstützen Sie die Validierung benutzerdefinierter Eigenschaften  
 ![CUIT&#95;Props](../test/media/cuit_props.png "CUIT_Props")  
  
1.  Überschreiben Sie die zugreifbare <xref:System.Windows.Forms.AccessibleObject.Description%2A>-Eigenschaft des Kurvenlegendenobjekts, um Werte von Rich-Eigenschaften aus der Beschreibungszeichenfolge zu übergeben (durch Semikolons (;) von der Hauptbeschreibung und voneinander getrennt, wenn mehrere Eigenschaften implementiert werden).  
  
    ```csharp  
    public class CurveLegendAccessibleObject : AccessibleObject  
    {  
        // add the state property value to the description  
        public override string Description  
        {  
            get  
            {  
                // Add ";" and the state value to the end  
                // of the curve legend's description  
                return "CurveLegend; " + State.ToString();  
            }  
        }  
    }  
    ```  
  
2.  Erstellen Sie ein UI-Test-Erweiterungspaket für das Steuerelement, indem Sie ein Klassenbibliotheksprojekt erstellen und Verweise auf Barrierefreiheit, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common sowie Microsoft.VisualStudio.TestTools.Extension hinzufügen. Ändern Sie für die Barrierefreiheit **Interoptypen einbetten** zu **FALSE**.  
  
3.  Fügen Sie eine von <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> abgeleitete Eigenschaftenanbieterklasse hinzu.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using Accessibility;  
    using Microsoft.VisualStudio.TestTools.UITesting;  
    using Microsoft.VisualStudio.TestTools.UITest.Extension;  
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
    using Microsoft.VisualStudio.TestTools.UITest.Common;  
  
    namespace ChartControlExtensionPackage  
    {  
        public class ChartControlPropertyProvider : UITestPropertyProvider  
        {  
        }  
    }  
    ```  
  
4.  Implementieren Sie den Eigenschaftenanbieter, indem Sie Eigenschaftennamen und Eigenschaftendeskriptoren in <xref:System.Collections.Generic.Dictionary%602> einfügen.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
5.  Überschreiben Sie <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName>, um anzugeben, dass die Assembly steuerelementspezifische Unterstützung für das Steuerelement und dessen untergeordneten Elemente bietet.  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
6.  Überschreiben Sie die verbleibenden abstrakten Methoden von <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
7.  Fügen Sie ein von <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> abgeleitete Erweiterungspaketklasse hinzu.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
8.  Definieren Sie das `UITestExtensionPackage`-Attribut für die Assembly.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
9. Überschreiben Sie in der Erweiterungspaketklasse <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName>, um bei Anforderung eines Eigenschaftenanbieters die entsprechende Klasse zurückzugeben.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
10. Überschreiben Sie die verbleibenden abstrakten Methoden und Eigenschaften von <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
11. Erstellen Sie die Binärdateien, und kopieren Sie sie nach **%ProgramFiles%\Gemeinsame Dateien\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.  
  
> [!NOTE]
>  Dieses Erweiterungspaket wird auf jedes Steuerelement vom Typ „Text“ angewendet. Mehrere Steuerelemente des gleichen Typs müssen separat getestet werden, und Sie müssen die beim Aufzeichnen der Tests bereitzustellenden Erweiterungspakete verwalten.  
  
##  <a name="codegeneration"></a> Codegenerierung durch Implementierung einer Klasse zum Zugriff auf benutzerdefinierte Eigenschaften unterstützen  
 Wenn der Test-Generator für codierte UI aus einer Sitzungsaufzeichnung Code generiert, wird für den Zugriff auf die Steuerelemente die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>-Klasse verwendet.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 Wenn ein Eigenschaftenanbieter für den Zugriff auf die benutzerdefinierten Eigenschaften des Steuerelements implementiert wurde, können Sie hierfür eine spezialisierte Klasse hinzufügen, um den generierten Code zu vereinfachen.  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
### <a name="to-add-a-specialized-class-to-access-your-control"></a>So fügen Sie eine spezialisierte Klasse zum Zugriff auf das Steuerelement hinzu  
 ![CUIT&#95;CodeGen](../test/media/cuit_codegen.png "CUIT_CodeGen")  
  
1.  Implementieren Sie eine von <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> abgeleitete Klasse, und fügen in der Sucheigenschaftenauflistung des Konstruktors den Typ des Steuerelements hinzu.  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
2.  Implementieren Sie die benutzerdefinierten Eigenschaften des Steuerelements als Eigenschaften der Klasse.  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
3.  Überschreiben Sie die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName>-Methode des Eigenschaftenanbieters, um den Typ der neuen Klasse für die untergeordneten Kurvenlegendensteuerelemente zurückzugeben.  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
4.  Überschreiben Sie die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A>-Methode des Eigenschaftenanbieters, um den Typ der PropertyNames-Methode der neuen Klasse zurückzugeben.  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
##  <a name="intentawareactions"></a> Absichtsbewusste Aktionen durch Implementierung eines Aktionsfilters unterstützen  
 Beim Aufzeichnen eines Tests in Visual Studio werden alle Maus- und Tastaturereignisse erfasst. In einigen Fällen kann jedoch der Zweck der durch die Reihe von Maus- und Tastaturereignissen bewirkten Aktion verloren gehen. Wenn das Steuerelement beispielsweise AutoVervollständigen unterstützt, kann bei der Wiedergabe des Tests in einer anderen Umgebung der gleiche Satz von Maus- und Tastaturereignissen einen abweichenden Wert ergeben. Sie können ein Aktionsfilter-Plug-In hinzufügen, von dem die Reihe der Tastatur- und Mausereignisse durch eine einzelne Aktion ersetzt wird. Dadurch können Sie die zur Auswahl eines Werts führende Reihe von Tastatur- und Mausereignissen durch eine einzelne Aktion zum Festlegen des Wert ersetzen. Auf diese Weise können die aufgrund von AutoVervollständigen in verschiedenen Umgebungen auftretenden Unterschiede bei Tests der codierten UI vermieden werden.  
  
### <a name="to-support-intent-aware-actions"></a>So unterstützen Sie absichtbewusste Aktionen  
 ![CUIT&#95;Actions](../test/media/cuit_actions.png "CUIT_Actions")  
  
1.  Implementieren Sie eine von <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> abgeleitete Aktionsfilterklasse, von der die Eigenschaften <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> und <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> überschrieben werden.  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
2.  Überschreiben Sie <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>. In diesem Beispiel wird eine Doppelklickaktion durch eine Einzelklickaktion ersetzt.  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
3.  Fügen Sie den Aktionsfilter der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A>-Methode des Erweiterungspakets hinzu.  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
4.  Erstellen Sie die Binärdateien, und kopieren Sie sie nach „%ProgramFiles%\Gemeinsame Dateien\Microsoft Shared\VSTT\10.0\UITestExtensionPackages“.  
  
> [!NOTE]
>  Der Aktionsfilter ist nicht von der Implementierung der Barrierefreiheit oder vom Eigenschaftenanbieter abhängig.  
  
## <a name="debug-your-property-provider-or-action-filter"></a>Den Eigenschaftenanbieter oder Aktionsfilter debuggen  
 Der Eigenschaftenanbieter und Aktionsfilter werden in einem Erweiterungspaket implementiert, das vom Test-Generator für codierte UI in einem von der Anwendung getrennten Prozess geladen und ausgeführt wird.  
  
#### <a name="to-debug-your-property-provider-or-action-filter"></a>So debuggen Sie den Eigenschaftenanbieter oder Aktionsfilter  
  
1.  Erstellen Sie die Debugversion des Erweiterungspakets, und kopieren Sie die DLL- und PDB-Dateien nach „%ProgramFiles%\Gemeinsame Dateien\Microsoft Shared\VSTT\10.0\UITestExtensionPackages“.  
  
2.  Führen Sie die Anwendung aus (nicht im Debugger.)  
  
3.  Führen Sie den Test-Generator für codierte UI aus  
  
     `codedUITestBuilder.exe  /standalone`  
  
4.  Fügen Sie den Debugger an den codedUITestBuilder-Prozess an.  
  
5.  Legen Sie im Code Haltepunkte fest.  
  
6.  Erstellen Sie im Test-Generator für codierte UI Asserts zum Testen des Eigenschaftenanbieters und Aufzeichnungsaktionen zum Testen der Aktionsfilter.  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
### <a name="guidance"></a>Empfehlungen  
 [Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Forms.AccessibleObject>   
 [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)
