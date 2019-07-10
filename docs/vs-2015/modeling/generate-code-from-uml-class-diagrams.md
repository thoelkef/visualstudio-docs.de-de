---
title: Generieren von Code aus UML-Klassendiagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fa073c794e790974f7f749b9d6f2302e9ff0a230
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67692519"
---
# <a name="generate-code-from-uml-class-diagrams"></a>Generieren von Code aus UML-Klassendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden Sie zum Generieren von Visual c#-.NET-Code aus UML-Klassendiagrammen in Visual Studio die **Code generieren** Befehl. Standardmäßig generiert der Befehl einen C#-Typ für jeden UML-Typ, den Sie auswählen. Sie können dieses Verhalten ändern oder erweitern, indem Sie die Textvorlagen ändern oder kopieren, mit denen der Code generiert wird. Sie können ein anderes Verhalten für die Typen angeben, die in anderen Paketen im Modell enthalten sind.  

 Die **Code generieren** Befehl ist besonders geeignet, zum Generieren von Code aus der Auswahl des Benutzers, der Elemente, und klicken Sie zum Generieren einer Datei für jede UML-Klasse oder ein anderes Element. Das folgende Bildschirmfoto zeigt z. B. zwei C#-Dateien, die aus zwei UML-Klassen generiert wurden.  

 Als Alternative können Sie ggf. zum Generieren von Code, in dem die generierten Dateien keine 1:1-Beziehung mit der UML-Elementen, Sie könnten das Verfassen von Textvorlagen, die aufgerufen werden, mit der **alle Vorlagen transformieren** Befehl. Weitere Informationen zu dieser Methode finden Sie unter [Generieren von Dateien aus einem UML-Modell](../modeling/generate-files-from-a-uml-model.md).  

 ![UML-Klasse, Diagramm und die generierten C&#35; Klassendateien. ](../modeling/media/oob-gencode1.png "oob_GenCode1")  

 Weitere Informationen zu UML-Klassendiagrammen in Visual Studio finden Sie unter den folgenden Themen:  

- [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)  

- [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)  

  Welche Versionen von Visual Studio UML-Klassendiagramme unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

## <a name="using-the-generate-code-command"></a>Verwenden des Befehls 'Code generieren'  
 Das folgende Verfahren beschreibt das Standardverhalten der **Code generieren** Befehl:  

#### <a name="to-generate-a-separate-file-for-each-element"></a>So generieren Sie eine separate Datei für jedes Element  

1. Erstellen Sie ein UML-Modell, das Klassen enthält. Sie können Stereotype auf die Modellelemente anwenden.  

    Weitere Informationen finden Sie unter [Standardcodegenerierung](#default).  

2. In einem Klassendiagramm oder im **UML-Modell-Explorer**, auswählen von Elementen, die von dem Sie Code generieren möchten. Es stehen Ihnen folgende Auswahlmöglichkeiten zur Verfügung:  

   - Ein bestimmter Satz von Elementen.  

   - Ein Paket oder das Modell, aus dessen Inhalt Code generiert werden soll.  

   - Das Diagramm, in dem alle Elemente ausgewählt werden können.  

3. Öffnen Sie das Kontextmenü für ein ausgewähltes Element, und wählen Sie dann **Code generieren**.  

    Beim ersten, mit denen Sie **Code generieren** in einem bestimmten Modell wird ein Dialogfeld angezeigt wird. In diesem Dialogfeld können Sie die Codegenerierungsparameter des Modells bearbeiten.  

    Wählen Sie **OK** , wenn Sie wissen, dass Sie diese Parameter ändern möchten.  

    Um später in diesem Dialogfeld zurückzukehren, öffnen Sie **UML-Modell-Explorer**. Öffnen Sie die Modellierung Kontextmenü, und wählen Sie dann **Codegenerierung einrichten**. Weitere Informationen finden Sie unter [Anpassen der Befehls ' Code generieren '](#custom).  

   Dateien werden generiert, die C#-Code enthalten sind. Im Standardfall wird eine Datei für jeden Typ generiert, und die Dateien werden in einem C#-Klassenbibliotheksprojekt generiert. Sie können dieses Verhalten jedoch anpassen. Weitere Informationen finden Sie unter [Anpassen der Befehls ' Code generieren '](#custom).  

   Einige Validierungstests werden für das Modell angewendet, um sicherzustellen, dass es in C# übersetzt werden kann. Wenn diese Tests fehlschlagen, wird eine Fehlermeldung angezeigt, und die Codegenerierung wird nicht ausgeführt. Wenn Sie einen Validierungsmenübefehl erstellt haben, wird Code für kein Element generiert, für das der Validierungsbefehl fehlschlägt. Weitere Informationen finden Sie unter [Definieren von validierungseinschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md).  

## <a name="default"></a> Standardcodegenerierung  
 In diesem Abschnitt werden die Ergebnisse, die von erstellt sind zusammengefasst die **Code generieren** Befehl, es sei denn, Sie den Befehl nicht angepasst. Weitere Informationen finden Sie unter [Anpassen der Befehls ' Code generieren '](#custom).  

- Ein C#-Typ wird für jeden Typ erzeugt, den Sie im UML-Modell ausgewählt haben. Jeder Typ befindet sich in einer separaten Codedatei unter dem **GeneratedCode** Ordner.  

- Wenn der UML-Typ in einem Paket enthalten ist, wird der generierte C#-Typ in einem Namespace platziert, und die Datei wird in einem Ordner generiert, der den gleichen Namen wie der Namespace hat.  

- Eine C#-Eigenschaft wird für jedes `Attribute` einer UML-Klasse generiert.  

- Eine C#-Methode wird für jede `Operation` eines UML-Typs generiert.  

- Ein C#-Feld wird für jede navigierbare Zuordnung generiert, an der die Klasse teilnimmt.  

  Sie können mehr Eigenschaften des generierten C#-Typs steuern, indem Sie jedem UML-Typ ein Stereotyp hinzufügen.  

|**Zum Erstellen dieses C#-Typs**|**Zeichnen Sie diesen UML-Typ**|**Übernehmen Sie dieses stereotype**|  
|---------------------------------|----------------------------|-------------------------------|  
|Klasse|Klasse|\<keine > oder<br /><br /> C#-Klasse|  
|Interface|Interface|\<keine > oder<br /><br /> C#-Schnittstelle|  
|Enumeration|Enumeration|\<keine > oder<br /><br /> C#-Enumeration|  
|delegate|Klasse|C#-Delegat|  
|Struktur|Klasse|C#-Struktur|  

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>So legen Sie ein Stereotyp für einen Typ oder ein anderes Element fest  

1. Öffnen Sie das Kontextmenü für das Element in einem Diagramm oder im **UML-Modell-Explorer**, und wählen Sie dann **Eigenschaften**.  

2. In der **Eigenschaften** Fenster, wählen Sie den Dropdown-Pfeil in der **Stereotype** -Eigenschaft, und wählen Sie dann das Kontrollkästchen für den Stereotyp, den Sie anwenden möchten.  

   > [!TIP]
   > Wenn die C#-Stereotype nicht angezeigt werden, aktivieren Sie das C#-Profil für das Modell oder ein Paket, das die Modellelemente enthält, für die Sie sich interessieren. Wählen Sie das Paket oder der Stamm des Modells in **UML-Modell-Explorer**. Klicken Sie dann in der **Eigenschaften** Fenster wählen **Profil**, und aktivieren Sie dann das C#-Profil.  

3. Erweitern Sie die **Stereotype** Eigenschaft, um die zusätzlichen Eigenschaften anzuzeigen, die Sie festlegen können.  

   Die **Beschreibung** Eigenschaften von Typen, Attribute, Vorgänge und Zuordnungen werden geschrieben, um `<summary>` Kommentare im generierten Code. Kommentarelemente, die mit Typen verknüpft sind, werden in `<remarks>`-Kommentare geschrieben.  

## <a name="varying-the-generated-code"></a>Variieren des generierten Codes  
 Der generierte Code unterscheidet sich je nach den Eigenschaften der einzelnen Typen, Attribute oder Vorgänge. Wenn Sie festlegen, z. B. die **Is Abstract** Eigenschaft einer Klasse auf "true", und klicken Sie dann die `abstract` Schlüsselwort wird für die generierte Klasse angezeigt. Setzen Sie die **Multiplizität** eines Attributs auf **0..\*** , und klicken Sie dann die generierte Eigenschaft eine `IEnumerable<>` Typ.  

 Außerdem stellt jedes Stereotyp mehrere zusätzliche Eigenschaften bereit, die Sie festlegen können. Diese Werte werden im C#-Code in geeignete Schlüsselwörter übersetzt. Wenn Sie z. B. die `Is Static`-Eigenschaft für eine Klasse festlegen, ist die C#-Klasse `static`.  

 Wählen Sie die Klasse oder ein anderes Element im Diagramm aus, um diese zusätzlichen Eigenschaften festzulegen. Erweitern Sie im Eigenschaftenfenster **Stereotype**, und erweitern Sie das C#-Stereotyp, z. B. **c#-Klasse**.  Für Klassen schließen diese zusätzlichen Eigenschaften Folgendes ein:  

- CRL-Attribute  

- Ist Partial  

- Is Static  

- Is Unsafe  

- Paketsichtbarkeit  

  Jedes Attribut und jeder Vorgang verfügt ebenfalls über Stereotypeigenschaften, die Sie festlegen können. Wenn Sie die Eigenschaften nicht auf einem neuen Attribut sehen, führen Sie **Code generieren**.  

## <a name="custom"></a> Anpassen der Befehls ' Code generieren '  
 Die **Code generieren** Befehl funktioniert, indem die Modellelemente, die mithilfe eines Satzes von Textvorlagen transformiert. Weitere Informationen zu Textvorlagen finden Sie unter [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).  

 Die Vorlagen werden in einem Satz von angegeben *textvorlagenbindungen*. Eine textvorlagenbindung gibt an, welche Vorlage angewendet werden soll, in dem die generierte Ausgabe eingefügt werden soll, und anderen Parametern der **Code generieren** Befehl.  

 Beim ersten Ausführen der **Code generieren** Befehl für ein bestimmtes Modell, in das Stammverzeichnis des Modells wird einen Standardsatz von vorlagenbindungen angefügt. Diese Bindungen gelten für alle Elemente im Modell.  

 Sie können diese Standardbindungen jedoch überschreiben und durch Anfügen von eigenen Bindungen an Pakete, Klassen oder andere Elemente ergänzen. Eine Bindung gilt für alle Elemente, die in dem Element enthalten sind, an das es angefügt wird. Wenn z. B. alle Typen in einem bestimmten Paket von einem anderen Satz von Vorlagen transformiert oder in einen anderen Ordner ausgegeben werden sollen, können Sie dem Paket Vorlagenbindungen anfügen.  

 Wählen Sie die Auslassungspunkte, um auf ein Modellelement angefügten vorlagenbindungen zu überprüfen, **[...]**  in die **Text Template Bindings** Eigenschaft im Eigenschaftenfenster angezeigt.  

 Die **Code generieren** Befehl wendet die Vorlagen auf jedes Modellelement, das Sie ausgewählt haben. Für jedes Element ist der angewendete Satz von Vorlagen, der kombinierte Vorlagensatz, der seinen Containern angefügt wurde, einschließlich des Modellstamms.  

 Wenn zwei Vorlagenbindungen in diesem Satz den gleichen Namen aufweisen, überschreibt die Bindung im kleineren Container die Bindung im größeren Container. Der Modellstamm besitzt z. B. eine Bindung mit dem Namen **-Klassenvorlage**. Um eine eigene Vorlage, die auf den Inhalt eines bestimmten Pakets angewendet haben, definieren Sie eine eigene vorlagenbindung mit dem Namen **-Klassenvorlage**.  

 Für ein Modellelement können mehrere Vorlagen übernommen werden. Sie können mehr als eine Datei aus jedem Modellelement generieren.  

> [!NOTE]
> Die Bindungen am Stamm des Modells fungieren für alle Elemente im Modell als Standard. Öffnen Sie zum Anzeigen dieser standardbindungen **UML-Modell-Explorer**. Öffnen Sie das Modellierungsprojekt-Kontextmenü, und wählen Sie dann **Codegenerierung einrichten**. Alternativ können Sie den Stamm des Modells im UML-Modell-Explorer auswählen. Wählen Sie im Eigenschaftenfenster **[...]**  in die **Text Template Bindings** Eigenschaft. Die Bindungen werden nicht angezeigt, bis Sie verwendet haben, die **Code generieren** mindestens einmal Befehl. Vorlagenbindungen können keinem Diagramm angefügt werden.  

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>So fügen Sie Textvorlagenbindungen an ein Paket oder anderes Modellelement an  

1. In **UML-Modell-Explorer**, öffnen Sie das Kontextmenü für ein Modellelement aus, und wählen Sie dann **Eigenschaften**. Im Allgemeinen fügen Sie Textvorlagenbindungen einem Paket oder dem Stamm des Modells an.  

2. In der **Eigenschaften** Fenster, wählen Sie die Schaltfläche mit den Auslassungspunkten ( **[...]** ) in der **Text Template Bindings** Eigenschaft.  

    Die **Text Template Bindings** Dialogfeld wird angezeigt.  

3. Wählen Sie **hinzufügen** um eine neue textvorlagenbindung zu erstellen.  

    \- oder –  

    Klicken Sie auf eine vorhandene Bindung, um sie zu bearbeiten.  

    Jede Vorlagenbindung definiert, wie eine angegebene Vorlage für das ausgewählt Modellelement und andere darin enthaltene Modellelemente übernommen werden soll.  

4. Legen Sie im Dialogfeld die Eigenschaften der Textvorlagenbindung fest.  

   |    **Property**    |                                                                                                                                                                                                                                                                                                                    **Beschreibung**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Name        |                                                                                                                                                                                                                                                  Ein Name für diese Bindung. Um eine von einem enthaltenden Paket oder Modell geerbte Bindung zu überschreiben, verwenden Sie den gleichen Namen wie die Bindung, die Sie überschreiben möchten.                                                                                                                                                                                                                                                  |
   |     Overwrite      |                                                                                                                                                                                                                                                                                                      Bei "true" wird jeder vorhandener Code überschrieben.                                                                                                                                                                                                                                                                                                       |
   |    Target Name     | Der Name der generierten Datei.<br /><br /> Sie können Ausdrücke wie z. B. in dieser Zeichenfolge einfügen `{Name}` oder `{Owner.Name}`. Sie können z. B. schreiben: `{Owner.Name}_{Name}`. Der Ausdruck wird für das Modellelement ausgewertet. Eigenschaften von Elementen, jedoch keine Methoden können verwendet werden. Welche Eigenschaften verwendet werden können, finden Sie unter den Eigenschaften der Typen in **Microsoft.VisualStudio.Uml.\*** . \*\*Wichtig:\* \* `{Name}` oder `{Owner.Name}` kann verwendet werden, nur in der **Zielname** Eigenschaft. Um den Namen der generierten Klasse zu ändern, müssen Sie die Vorlage ändern. Weitere Informationen finden Sie unter [Schreiben einer Textvorlage](#writing). |
   |    Project Path    |                                                                      Gibt den Pfad zum [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekt an, das die Ausgabedateien der Transformation enthält. Verwenden Sie typisierte Werte, um ein neues Projekt zu erstellen. Wählen Sie die Schaltfläche mit den Auslassungspunkten ( **[...]** ) auf ein vorhandenes Projekt auszuwählen.<br /><br /> Falls noch nicht vorhanden, wird ein neues Projekt erstellt. Es ist ein C#-Klassenbibliotheksprojekt.<br /><br /> Hierzu müssen Sie das Projekt direkt eingeben. Sie können Umgebungsvariablenmakros wie %ProgramFiles% oder %LocalAppData% einschließen.                                                                       |
   |  Target Directory  |                                                                                          Der Ordner, in dem die Zieldatei generiert wird. Der Pfad ist relativ zum Projektordner.<br /><br /> Sie können mithilfe des `{PackageStructure}`-Ausdrucks einen Pfad einfügen, der den Namen der enthaltenden Pakete entspricht. Der Standardwert ist `\GeneratedCode\{PackageStructure}`. Sie können auch Umgebungsvariablen wie %TEMP% oder %HomePath% einschließen. **Wichtig:** `{PackageStructure}` kann verwendet werden, nur in der **Zielverzeichnis** Eigenschaft.                                                                                          |
   | Vorlagendatei-Pfad |                                                                                                                                                           Die Vorlage, mit der die Transformation ausgeführt wird.<br /><br /> Sie können entweder die bereitgestellten Vorlagen verwenden oder eigene erstellen. Sie finden die bereitgestellten Vorlagen am folgenden Speicherort:<br /><br /> …\Programme\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |

5. Sie können einem Element beliebig viele Bindungen anfügen.  

## <a name="writing"></a> Schreiben einer Textvorlage  
 Sie können eigene Textvorlagen schreiben. Textvorlagen können Programmcode oder eine beliebige andere Art von Textdatei generieren.  

 Beginnen Sie am besten, indem Sie Kopien der Standardvorlagen ändern. Sie können die Vorladen aus den folgenden Speicherorten kopieren:  

 …\Programme\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\  

 Erläuterungen zu den Textvorlagen finden Sie unter den folgenden Themen.  

- Eine Textvorlage ist ein Prototyp der resultierenden Datei und enthält sowohl den resultierenden Text als auch den Programmcode, der das Modell liest. Weitere Informationen finden Sie unter [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).  

- Sie müssen die UML-API verwenden, um im Programmcode im Modell zu navigieren. Weitere Informationen finden Sie unter [Navigieren im UML-Modell](../modeling/navigate-the-uml-model.md) und [-API-Referenz für UML-UML-Modellierungserweiterbarkeit](../modeling/api-reference-for-uml-modeling-extensibility.md).  

  Verwenden Sie die Vorlagen mit der **Code generieren** Befehls müssen Sie die Modeling-Anweisung einschließen. Zum Beispiel:  

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`  

  Das `ElementType`-Attribut definiert den Typ des UML-Elements, auf das diese Vorlage angewendet wird.  

  In der Vorlage gehört `this` zu einer temporären Klasse, die über die folgenden Eigenschaften verfügt:  

- `Element` = das UML-<xref:Microsoft.VisualStudio.Uml.Classes.IElement>, auf das die Vorlage angewendet wird.  

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>  

- `Host`: <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  

- `ModelBus`: <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>. Weitere Informationen finden Sie unter [Integrieren von UML-Modellen in andere Modelle und Tools](../modeling/integrate-uml-models-with-other-models-and-tools.md).  

- `ProfileName` = "C#Profile"  

- `ServiceProvider`: <xref:System.IServiceProvider>  

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.  

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Dies ist der Visualisierungs- und Modellierungs-SDK-Speicher, für den der UML-Modellspeicher implementiert wird. Verwenden Sie <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore> zum Abrufen des UML-`this.Element.GetModelStore()`.  

  Die folgenden Punkte können beim Schreiben der Textvorlage hilfreich sein. Diese Informationen werden ausführlich im [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).  

- Sie können die Dateinamenerweiterung des Ergebnisses in der `Output`-Anweisung festlegen. Eine `Output`-Direktive ist in jeder Textvorlage erforderlich.  

- Die Vorlage verweist automatisch auf einige Assemblys. Diese Assemblys schließen z. B. "System.dll" und "Microsoft.VisualStudio.Uml.Interfaces.dll" ein.  

   Für die Verwendung anderer Assemblys im generierenden Programmcode müssen Sie eine `Assembly`-Direktive verwenden. Zum Beispiel:  

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`  

- Einige Namespaces wie `System` werden automatisch in den Programmcode importiert. Für andere Namespaces können Sie die `Import`-Anweisung auf die gleiche Weise verwenden wie eine `using`-Anweisung. Zum Beispiel:  

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`  

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`  

- Verwenden Sie die `Include`-Direktive, um auf den Text einer anderen Datei zu verweisen.  

- Die Teile der Vorlage, die in Klammern eingeschlossene `<# ... #>` werden ausgeführt, indem die **Code generieren** Befehl. Teile der Vorlage außerhalb dieser Klammern werden in die Ergebnisdatei kopiert. Es ist wichtig, zwischen dem generierenden Code und dem generierten Text zu unterscheiden. Der generierte Text kann jeder Sprache aufweisen.  

- `<#= Expressions #>` werden ausgewertet und in Zeichenfolgen konvertiert.  

## <a name="see-also"></a>Siehe auch  
 [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)   
 [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)   
 [Generieren von Dateien von einem UML-Modell](../modeling/generate-files-from-a-uml-model.md)
