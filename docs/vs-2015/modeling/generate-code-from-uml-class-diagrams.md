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
ms.openlocfilehash: 23cefa3d072c2e582237152bff77a2271046053d
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871828"
---
# <a name="generate-code-from-uml-class-diagrams"></a>Generieren von Code aus UML-Klassendiagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um Visual C# .NET-Code aus UML-Klassendiagrammen in Visual Studio zu generieren, verwenden Sie den Befehl **Code generieren** . Standardmäßig generiert der Befehl einen C#-Typ für jeden UML-Typ, den Sie auswählen. Sie können dieses Verhalten ändern oder erweitern, indem Sie die Textvorlagen ändern oder kopieren, mit denen der Code generiert wird. Sie können ein anderes Verhalten für die Typen angeben, die in anderen Paketen im Modell enthalten sind.

 Der Befehl **Code generieren** ist besonders für das Generieren von Code aus der Auswahl von Elementen des Benutzers und das Generieren einer Datei für jede UML-Klasse oder ein anderes Element geeignet. Das folgende Bildschirmfoto zeigt z. B. zwei C#-Dateien, die aus zwei UML-Klassen generiert wurden.

 Wenn Sie Code generieren möchten, in dem die generierten Dateien nicht über eine 1:1-Beziehung mit den UML-Elementen verfügen, können Sie Alternativtext Vorlagen schreiben, die mit dem Befehl **Transform all Templates** aufgerufen werden. Weitere Informationen zu dieser Methode finden Sie unter [Generieren von Dateien aus einem UML-Modell](../modeling/generate-files-from-a-uml-model.md).

 ![UML-Klassendiagramm und generierte&#35; C-Klassendateien.](../modeling/media/oob-gencode1.png "oob_GenCode1")

 Weitere Informationen zu UML-Klassendiagrammen in Visual Studio finden Sie unter den folgenden Themen:

- [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)

- [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)

  Welche Versionen von Visual Studio UML-Klassendiagramme unterstützen, erfahren Sie unter [Versions Unterstützung für Architektur-und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="using-the-generate-code-command"></a>Verwenden des Befehls 'Code generieren'
 Im folgenden Verfahren wird das Standardverhalten des Befehls **Code generieren** beschrieben:

#### <a name="to-generate-a-separate-file-for-each-element"></a>So generieren Sie eine separate Datei für jedes Element

1. Erstellen Sie ein UML-Modell, das Klassen enthält. Sie können Stereotype auf die Modellelemente anwenden.

    Weitere Informationen finden Sie unter [Standard Code Generierungs Transformationen](#default).

2. Wählen Sie in einem Klassendiagramm oder im **UML-Modell-Explorer**Elemente aus, aus denen Sie Code generieren möchten. Es stehen Ihnen folgende Auswahlmöglichkeiten zur Verfügung:

   - Ein bestimmter Satz von Elementen.

   - Ein Paket oder das Modell, aus dessen Inhalt Code generiert werden soll.

   - Das Diagramm, in dem alle Elemente ausgewählt werden können.

3. Öffnen Sie das Kontextmenü für ein ausgewähltes Element, und wählen Sie dann **Code generieren**aus.

    Wenn Sie zum ersten Mal Code in einem bestimmten Modell **generieren** , wird ein Dialogfeld angezeigt. In diesem Dialogfeld können Sie die Codegenerierungsparameter des Modells bearbeiten.

    Wählen Sie **OK** aus, wenn Sie nicht wissen, dass Sie diese Parameter ändern möchten.

    Um später zu diesem Dialogfeld zurückzukehren, öffnen Sie den **UML-Modell-Explorer**. Öffnen Sie das Kontextmenü für das Modellierungsprojekt, und wählen Sie dann **Code Generierung einrichten**aus. Weitere Informationen finden Sie unter [Anpassen des Befehls "Code generieren](#custom)".

   Dateien werden generiert, die C#-Code enthalten sind. Im Standardfall wird eine Datei für jeden Typ generiert, und die Dateien werden in einem C#-Klassenbibliotheksprojekt generiert. Sie können dieses Verhalten jedoch anpassen. Weitere Informationen finden Sie unter [Anpassen des Befehls "Code generieren](#custom)".

   Einige Validierungstests werden für das Modell angewendet, um sicherzustellen, dass es in C# übersetzt werden kann. Wenn diese Tests fehlschlagen, wird eine Fehlermeldung angezeigt, und die Codegenerierung wird nicht ausgeführt. Wenn Sie einen Validierungsmenübefehl erstellt haben, wird Code für kein Element generiert, für das der Validierungsbefehl fehlschlägt. Weitere Informationen finden Sie unter [Definieren von Validierungs Einschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="default"></a>Standardmäßige Code Generierungs Transformationen
 In diesem Abschnitt werden die Ergebnisse zusammengefasst, die vom Befehl **Code generieren** erzeugt werden, es sei denn, Sie passen den Befehl an. Weitere Informationen finden Sie unter [Anpassen des Befehls "Code generieren](#custom)".

- Ein C#-Typ wird für jeden Typ erzeugt, den Sie im UML-Modell ausgewählt haben. Jeder Typ wird in eine separate Codedatei im Ordner **generatedcode** eingefügt.

- Wenn der UML-Typ in einem Paket enthalten ist, wird der generierte C#-Typ in einem Namespace platziert, und die Datei wird in einem Ordner generiert, der den gleichen Namen wie der Namespace hat.

- Eine C#-Eigenschaft wird für jedes `Attribute` einer UML-Klasse generiert.

- Eine C#-Methode wird für jede `Operation` eines UML-Typs generiert.

- Ein C#-Feld wird für jede navigierbare Zuordnung generiert, an der die Klasse teilnimmt.

  Sie können mehr Eigenschaften des generierten C#-Typs steuern, indem Sie jedem UML-Typ ein Stereotyp hinzufügen.

|**So erstellen Sie C# diesen Typ**|**Diesen UML-Typ zeichnen**|**Dieses Stereotyp anwenden**|
|---------------------------------|----------------------------|-------------------------------|
|Klasse|Klasse|\<keine > oder<br /><br /> C#-Klasse|
|Interface|Interface|\<keine > oder<br /><br /> C#-Schnittstelle|
|Enumeration|Enumeration|\<keine > oder<br /><br /> C#-Enumeration|
|delegate|Klasse|C#-Delegat|
|Struktur|Klasse|C#-Struktur|

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>So legen Sie ein Stereotyp für einen Typ oder ein anderes Element fest

1. Öffnen Sie das Kontextmenü für das Element in einem Diagramm oder im **UML-Modell-Explorer**, und wählen Sie dann **Eigenschaften**aus.

2. Klicken Sie im Fenster **Eigenschaften** auf den Dropdown Pfeil in der **Stereotype** -Eigenschaft, und aktivieren Sie dann das Kontrollkästchen für das Stereotyp, das Sie anwenden möchten.

   > [!TIP]
   > Wenn die C#-Stereotype nicht angezeigt werden, aktivieren Sie das C#-Profil für das Modell oder ein Paket, das die Modellelemente enthält, für die Sie sich interessieren. Wählen Sie das Paket oder den Stamm des Modells im **UML-Modell-Explorer**aus. Wählen Sie dann im Fenster **Eigenschaften** die Option **Profil**aus, und aktivieren C# Sie dann das Profil.

3. Erweitern Sie die Eigenschaft **Stereotype** , um die zusätzlichen Eigenschaften anzuzeigen, die Sie festlegen können.

   Die **Beschreibungs** Eigenschaften von Typen, Attributen, Vorgängen und Zuordnungen werden `<summary>` in Kommentare im generierten Code geschrieben. Kommentarelemente, die mit Typen verknüpft sind, werden in `<remarks>`-Kommentare geschrieben.

## <a name="varying-the-generated-code"></a>Variieren des generierten Codes
 Der generierte Code unterscheidet sich je nach den Eigenschaften der einzelnen Typen, Attribute oder Vorgänge. Wenn Sie z. b. die **is Abstract** -Eigenschaft einer Klasse auf true festlegen, wird `abstract` das-Schlüsselwort in der generierten-Klasse angezeigt. Wenn Sie die Multiplizität eines Attributs auf **0..\*** festlegen, wird die generierte Eigenschaft über einen `IEnumerable<>` -Typ verfügen.

 Außerdem stellt jedes Stereotyp mehrere zusätzliche Eigenschaften bereit, die Sie festlegen können. Diese Werte werden im C#-Code in geeignete Schlüsselwörter übersetzt. Wenn Sie z. B. die `Is Static`-Eigenschaft für eine Klasse festlegen, ist die C#-Klasse `static`.

 Wählen Sie die Klasse oder ein anderes Element im Diagramm aus, um diese zusätzlichen Eigenschaften festzulegen. Erweitern Sie im Eigenschaftenfenster **Stereotype**, und erweitern Sie dann C# das Stereotyp, z. b.  **C# Klasse**.  Für Klassen schließen diese zusätzlichen Eigenschaften Folgendes ein:

- CRL-Attribute

- Ist Partial

- Is Static

- Is Unsafe

- Paketsichtbarkeit

  Jedes Attribut und jeder Vorgang verfügt ebenfalls über Stereotypeigenschaften, die Sie festlegen können. Wenn die Eigenschaften für ein neues Attribut nicht angezeigt werden, führen Sie **Code generieren**aus.

## <a name="custom"></a>Anpassen des Befehls "Code generieren"
 Der Befehl **Code generieren** funktioniert, indem die Modellelemente mithilfe eines Satzes von Textvorlagen transformiert werden. Weitere Informationen zu Textvorlagen finden Sie unter [Code Generierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).

 Die Vorlagen werden in einem Satz von *Textvorlagen Bindungen*angegeben. Eine Textvorlagen Bindung gibt an, welche Vorlage angewendet werden soll, wo die generierte Ausgabe abgelegt werden soll, und andere Parameter des Befehls " **Code generieren** ".

 Wenn Sie den Befehl **Code generieren** für ein bestimmtes Modell zum ersten Mal ausführen, wird ein Standardsatz von Vorlagen Bindungen an den Stamm des Modells angefügt. Diese Bindungen gelten für alle Elemente im Modell.

 Sie können diese Standardbindungen jedoch überschreiben und durch Anfügen von eigenen Bindungen an Pakete, Klassen oder andere Elemente ergänzen. Eine Bindung gilt für alle Elemente, die in dem Element enthalten sind, an das es angefügt wird. Wenn z. B. alle Typen in einem bestimmten Paket von einem anderen Satz von Vorlagen transformiert oder in einen anderen Ordner ausgegeben werden sollen, können Sie dem Paket Vorlagenbindungen anfügen.

 Um die an ein Modellelement angefügten Vorlagen Bindungen zu überprüfen, wählen Sie die Auslassungs Punkte **[...]** in der Eigenschaft **Text Vorlagen Bindungen** in der Eigenschaftenfenster aus.

 Der Befehl **Code generieren** wendet Vorlagen auf jedes Modellelement an, das Sie ausgewählt haben. Für jedes Element ist der angewendete Satz von Vorlagen, der kombinierte Vorlagensatz, der seinen Containern angefügt wurde, einschließlich des Modellstamms.

 Wenn zwei Vorlagenbindungen in diesem Satz den gleichen Namen aufweisen, überschreibt die Bindung im kleineren Container die Bindung im größeren Container. Der Modell Stamm hat z. b. eine Bindung mit der Name- **Klassen Vorlage**. Wenn Sie Ihre eigene Vorlage auf den Inhalt eines bestimmten Pakets anwenden möchten, definieren Sie eine eigene Vorlagen Bindung mit der Name- **Klassen Vorlage**.

 Für ein Modellelement können mehrere Vorlagen übernommen werden. Sie können mehr als eine Datei aus jedem Modellelement generieren.

> [!NOTE]
> Die Bindungen am Stamm des Modells fungieren für alle Elemente im Modell als Standard. Um diese Standard Bindungen anzuzeigen, öffnen Sie den **UML-Modell-Explorer**. Öffnen Sie das Kontextmenü des Modellierungs Projekts, und wählen Sie dann **Code Generierung einrichten**. Alternativ können Sie den Stamm des Modells im UML-Modell-Explorer auswählen. Wählen Sie in der Eigenschaftenfenster in der Eigenschaft **Text Vorlagen Bindungen** den Wert **[...]** aus. Die Bindungen werden erst angezeigt, wenn Sie den Befehl **Code generieren** mindestens einmal verwendet haben. Vorlagenbindungen können keinem Diagramm angefügt werden.

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>So fügen Sie Textvorlagenbindungen an ein Paket oder anderes Modellelement an

1. Öffnen Sie im **UML-Modell-Explorer**das Kontextmenü für ein Modellelement, und wählen Sie dann **Eigenschaften**aus. Im Allgemeinen fügen Sie Textvorlagenbindungen einem Paket oder dem Stamm des Modells an.

2. Wählen Sie im Fenster **Eigenschaften** die Schaltfläche mit den Auslassungs Zeichen ( **[...]** ) in der Eigenschaft **Text Vorlagen Bindungen** aus.

    Das Dialogfeld **Text Vorlagen Bindungen** wird angezeigt.

3. Wählen Sie **Hinzufügen** aus, um eine neue Textvorlagen Bindung zu erstellen.

    \- oder –

    Klicken Sie auf eine vorhandene Bindung, um sie zu bearbeiten.

    Jede Vorlagenbindung definiert, wie eine angegebene Vorlage für das ausgewählt Modellelement und andere darin enthaltene Modellelemente übernommen werden soll.

4. Legen Sie im Dialogfeld die Eigenschaften der Textvorlagenbindung fest.

   |    **Property**    |                                                                                                                                                                                                                                                                                                                    **Beschreibung**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Name        |                                                                                                                                                                                                                                                  Ein Name für diese Bindung. Um eine von einem enthaltenden Paket oder Modell geerbte Bindung zu überschreiben, verwenden Sie den gleichen Namen wie die Bindung, die Sie überschreiben möchten.                                                                                                                                                                                                                                                  |
   |     Overwrite      |                                                                                                                                                                                                                                                                                                      Bei "true" wird jeder vorhandener Code überschrieben.                                                                                                                                                                                                                                                                                                       |
   |    Target Name     | Der Name der generierten Datei.<br /><br /> Sie können Ausdrücke in diese Zeichenfolge einfügen, `{Name}` z `{Owner.Name}`. b. oder. Sie könnten z. b. Folgendes `{Owner.Name}_{Name}`schreiben:. Der Ausdruck wird für das Modellelement ausgewertet. Eigenschaften von Elementen, jedoch keine Methoden können verwendet werden. Informationen zu den Eigenschaften, die verwendet werden können, finden Sie in den Eigenschaften der Typen in **Microsoft. VisualStudio\*. Uml.** . \*\*Wichtig:\* \* oderkann`{Owner.Name}` nur in der Eigenschaft Zielname verwendet werden. `{Name}` Um den Namen der generierten Klasse zu ändern, müssen Sie die Vorlage ändern. Weitere Informationen finden Sie unter [Schreiben einer Text Vorlage](#writing). |
   |    Project Path    |                                                                      Gibt den Pfad zum [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekt an, das die Ausgabedateien der Transformation enthält. Verwenden Sie typisierte Werte, um ein neues Projekt zu erstellen. Wählen Sie die Schaltfläche mit den Auslassungs Punkten ( **[...]** ), um ein vorhandenes Projekt auszuwählen.<br /><br /> Falls noch nicht vorhanden, wird ein neues Projekt erstellt. Es ist ein C#-Klassenbibliotheksprojekt.<br /><br /> Hierzu müssen Sie das Projekt direkt eingeben. Sie können Umgebungsvariablenmakros wie %ProgramFiles% oder %LocalAppData% einschließen.                                                                       |
   |  Target Directory  |                                                                                          Der Ordner, in dem die Zieldatei generiert wird. Der Pfad ist relativ zum Projektordner.<br /><br /> Sie können mithilfe des `{PackageStructure}`-Ausdrucks einen Pfad einfügen, der den Namen der enthaltenden Pakete entspricht. Der Standardwert ist `\GeneratedCode\{PackageStructure}`. Sie können auch Umgebungsvariablen wie %TEMP% oder %HomePath% einschließen. **Wichtig:** `{PackageStructure}` kann nur in der **Zielverzeichnis** Eigenschaft verwendet werden.                                                                                          |
   | Vorlagendatei-Pfad |                                                                                                                                                           Die Vorlage, mit der die Transformation ausgeführt wird.<br /><br /> Sie können entweder die bereitgestellten Vorlagen verwenden oder eigene erstellen. Sie finden die bereitgestellten Vorlagen am folgenden Speicherort:<br /><br /> …\Programme\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |

5. Sie können einem Element beliebig viele Bindungen anfügen.

## <a name="writing"></a>Schreiben einer Text Vorlage
 Sie können eigene Textvorlagen schreiben. Textvorlagen können Programmcode oder eine beliebige andere Art von Textdatei generieren.

 Beginnen Sie am besten, indem Sie Kopien der Standardvorlagen ändern. Sie können die Vorladen aus den folgenden Speicherorten kopieren:

 …\Programme\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\

 Erläuterungen zu den Textvorlagen finden Sie unter den folgenden Themen.

- Eine Textvorlage ist ein Prototyp der resultierenden Datei und enthält sowohl den resultierenden Text als auch den Programmcode, der das Modell liest. Weitere Informationen finden Sie unter [Code Generierung und T4-Text Vorlagen](../modeling/code-generation-and-t4-text-templates.md).

- Sie müssen die UML-API verwenden, um im Programmcode im Modell zu navigieren. Weitere Informationen finden Sie unter [Navigieren im UML-Modell](../modeling/navigate-the-uml-model.md) und in der [API-Referenz für UML-Modellierungs Erweiterbarkeit](../modeling/api-reference-for-uml-modeling-extensibility.md).

  Um die Vorlagen mit dem Befehl **Code generieren** verwenden zu können, müssen Sie die Modeling-Direktive einschließen. Zum Beispiel:

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`

  Das `ElementType`-Attribut definiert den Typ des UML-Elements, auf das diese Vorlage angewendet wird.

  In der Vorlage gehört `this` zu einer temporären Klasse, die über die folgenden Eigenschaften verfügt:

- `Element`= das UML- [IElement](/previous-versions/dd516035(v=vs.140)) , auf das die Vorlage angewendet wird.

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>

- `Host`: [Itexttemplatingenginehost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

- `ModelBus`: [ModelBus](/previous-versions/ee904639(v=vs.140)). Weitere Informationen finden Sie unter [integrieren von UML-Modellen in andere Modelle und Tools](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- `ProfileName` = "C#Profile"

- `ServiceProvider`: <xref:System.IServiceProvider>

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Dies ist der Visualisierungs- und Modellierungs-SDK-Speicher, für den der UML-Modellspeicher implementiert wird. Verwenden`this.Element.GetModelStore()`Sie zum Abrufen des UML- [imodelstores](/previous-versions/ee789385(v=vs.140)).

  Die folgenden Punkte können beim Schreiben der Textvorlage hilfreich sein. Diese Informationen werden ausführlich unter [Code Generierung und T4-Text Vorlagen](../modeling/code-generation-and-t4-text-templates.md)beschrieben.

- Sie können die Dateinamenerweiterung des Ergebnisses in der `Output`-Anweisung festlegen. Eine `Output`-Direktive ist in jeder Textvorlage erforderlich.

- Die Vorlage verweist automatisch auf einige Assemblys. Diese Assemblys schließen z. B. "System.dll" und "Microsoft.VisualStudio.Uml.Interfaces.dll" ein.

   Für die Verwendung anderer Assemblys im generierenden Programmcode müssen Sie eine `Assembly`-Direktive verwenden. Zum Beispiel:

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`

- Einige Namespaces wie `System` werden automatisch in den Programmcode importiert. Für andere Namespaces können Sie die `Import`-Anweisung auf die gleiche Weise verwenden wie eine `using`-Anweisung. Zum Beispiel:

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`

- Verwenden Sie die `Include`-Direktive, um auf den Text einer anderen Datei zu verweisen.

- Die Teile der in eckige Klammern `<# ... #>` eingeschlossenen Vorlage werden vom Befehl **Code generieren** ausgeführt. Teile der Vorlage außerhalb dieser Klammern werden in die Ergebnisdatei kopiert. Es ist wichtig, zwischen dem generierenden Code und dem generierten Text zu unterscheiden. Der generierte Text kann jeder Sprache aufweisen.

- `<#= Expressions #>` werden ausgewertet und in Zeichenfolgen konvertiert.

## <a name="see-also"></a>Siehe auch
 [UML-Klassendiagramme: ](../modeling/uml-class-diagrams-reference.md) Verweis[auf UML-Klassendiagramme: Richt](../modeling/uml-class-diagrams-guidelines.md) Linien [Generieren von Dateien aus einem UML-Modell](../modeling/generate-files-from-a-uml-model.md)
