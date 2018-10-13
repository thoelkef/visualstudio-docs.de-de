---
title: Erstellen und Konfigurieren von Typmembern (Klassen-Designer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9a133b452000753eb5b7dfba579c8954791196b9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228331"
---
# <a name="creating-and-configuring-type-members-class-designer"></a>Erstellen und Konfigurieren von Typmembern (Klassen-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können diese Member zu Typen in einem Klassendiagramm hinzufügen und diese Member im Fenster **Klassendetails** konfigurieren:  
  
|**Type**|**Member, die der Typ enthalten kann**|  
|--------------|--------------------------------|  
|Klasse|Methode, Eigenschaft (bei C# und Visual Basic), Feld, Ereignis (bei C# und Visual Basic), Konstruktor (Methode), Destruktor (Methode), Konstante|  
|Enum|Member|  
|Interface|Methode, Eigenschaft, Ereignis (bei C# und Visual Basic)|  
|Abstrakte Klasse|Methode, Eigenschaft (bei C# und Visual Basic), Feld, Ereignis (bei C# und Visual Basic), Konstruktor (Methode), Destruktor (Methode), Konstante|  
|Struktur (Struct in C#)|Methode, Eigenschaft (bei C# und Visual Basic), Feld, Ereignis (bei C# und Visual Basic), Konstruktor (Methode), Konstante|  
|delegate|Parameter|  
|Modul (nur VB)|Methode, Eigenschaft, Feld, Ereignis, Konstruktor, Konstante|  
  
> [!NOTE]
>  Erhöhen Sie die Präzision von Eigenschaftsdeklarationen durch automatisch implementierte Eigenschaften (nur C#), wenn in den Get- und Set-Zugriffsmethoden der Eigenschaft keine zusätzliche Logik erforderlich ist. Um die vollständige Signatur anzuzeigen, wählen Sie im Menü **Klassendiagramm** die Option **Memberformat ändern** aus, und klicken anschließend auf **Vollständige Signatur anzeigen**. Weitere Informationen über automatisch implementierte Eigenschaften finden Sie unter [Automatisch implementierte Eigenschaften](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Unterstützender Inhalt|  
|----------|------------------------|  
|**Erste Schritte:** Bevor Sie Typmember erstellen und konfigurieren, müssen Sie das Fenster „Klassendetails“ öffnen.|-   [So öffnen Sie das Fenster „Klassendetails“](../ide/creating-and-configuring-type-members-class-designer.md#OpenClassDetails)<br />-   [Hinweise zur Verwendung von Klassendetails](../ide/creating-and-configuring-type-members-class-designer.md#ClassDetailsUsageNotes)<br />-   [Anzeige schreibgeschützter Informationen](../ide/creating-and-configuring-type-members-class-designer.md#ReadOnlyInfo)<br />-   [Tastenkombinationen und Mausaktionen im Klassendiagramm und Fenster „Klassendetails“ (Klassen-Designer)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md)|  
|**Erstellen und ändern Sie Typmember:** Sie können neue Member erstellen, Member ändern und einer Methode Parameter hinzufügen, indem Sie das Fenster „Klassendetails“ verwenden.|-   [Erstellen von Membern](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)<br />-   [Ändern von Typmembern](../ide/creating-and-configuring-type-members-class-designer.md#ModifyTypeMembers)<br />-   [Hinzufügen von Parametern zu Methoden](../ide/creating-and-configuring-type-members-class-designer.md#AddMethodParams)|  
  
##  <a name="OpenClassDetails"></a> So öffnen Sie das Fenster „Klassendetails“  
 Standardmäßig wird das Fenster „Klassendetails“ automatisch angezeigt, wenn Sie ein neues Klassendiagramm öffnen (siehe [Vorgehensweise: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)). Sie können das Klassendetailsfenster jedoch mit folgenden Methoden auch explizit öffnen.  
  
#### <a name="to-open-the-class-details-window"></a>So öffnen Sie das Klassendetailsfenster  
  
1.  Klicken Sie mit der rechten Maustaste auf eine Klasse im Diagramm, um ein Kontextmenü anzuzeigen.  
  
2.  Klicken Sie im Kontextmenü auf **Klassendetailsfenster**.  
  
 – oder –  
  
-   Zeigen Sie im Menü „Ansicht“ auf **Weitere Fenster**, und klicken Sie dann auf **Klassendetails**.  
  
##  <a name="CreateMembers"></a> Erstellen von Membern  
 Sie können einen Member mit einem der folgenden Tools erstellen:  
  
-   Klassen-Designer  
  
-   Symbolleiste des Klassendetailsfensters  
  
-   Klassendetailsfenster  
  
> [!NOTE]
>  Mit den in diesem Abschnitt beschriebenen Verfahren können Sie außerdem Konstruktoren und Destruktoren erstellen. Beachten Sie, dass es sich bei Konstruktoren und Destruktoren um spezielle Methodenformen handelt, die in Formen im Klassendiagramm im Depot **Methoden** und im Raster des Klassendetailsfenster im Abschnitt **Methoden** angezeigt werden.  
  
> [!NOTE]
>  Der Parameter ist die einzige Entität, die Sie einem Delegaten hinzufügen können. Das Verfahren 'So erstellen Sie einen Member mithilfe der Symbolleiste des Klassendetailsfensters' kann für diese Aktion nicht angewendet werden.  
  
#### <a name="to-create-a-member-using-class-designer"></a>So erstellen Sie einen Member mit dem Klassen-Designer  
  
1.  Klicken Sie mit der rechten Maustaste auf den Typ, dem Sie einen Member hinzufügen möchten, zeigen Sie auf **Hinzufügen**, und wählen Sie dann den hinzuzufügenden Membertyp aus.  
  
     Daraufhin wird eine neue Membersignatur erstellt und dem Typ hinzugefügt. Der Signatur wird ein Standardname zugewiesen, den Sie im **Klassen-Designer**, im Fenster **Klassendetails** oder im Fenster **Eigenschaften** ändern können.  
  
2.  Wahlweise können Sie weitere Memberdetails angeben, z. B. den Typ.  
  
#### <a name="to-create-a-member-using-the-class-details-window-toolbar"></a>So erstellen Sie einen Member mithilfe der Symbolleiste des Klassendetailsfensters  
  
1.  Wählen Sie auf der Diagrammoberfläche den Typ aus, dem Sie einen Member hinzufügen möchten.  
  
     Der Typ erhält den Fokus, und sein Inhalt wird im Klassendetailsfenster angezeigt.  
  
2.  Klicken Sie auf der Symbolleiste des Fensters „Klassendetails“ auf das obere Symbol, und wählen Sie **Neu \<Member>** aus der Dropdownliste aus.  
  
     Der Cursor wird in das Feld **Name** in einer Zeile für die gewünschte Art von Member verschoben. Wenn Sie z.B. auf **Neue Eigenschaft** klicken, wird der Cursor in eine neue Zeile im Abschnitt **Eigenschaften** des Klassendetailsfensters verschoben.  
  
3.  Geben Sie den Namen des zu erstellenden Members ein, und drücken Sie die EINGABETASTE (oder verschieben Sie den Fokus, z. B. durch Drücken der TAB-TASTE).  
  
     Daraufhin wird eine neue Membersignatur erstellt und dem Typ hinzugefügt. Der Member ist nun im Code vorhanden und wird im **Klassen-Designer**, im Klassendetailsfenster und im Eigenschaftenfenster angezeigt.  
  
4.  Wahlweise können Sie weitere Memberdetails angeben, z. B. den Typ.  
  
#### <a name="to-create-a-member-using-the-class-details-window"></a>So erstellen Sie einen Member im Klassendetailsfenster  
  
1.  Wählen Sie auf der Diagrammoberfläche den Typ aus, dem Sie einen Member hinzufügen möchten.  
  
     Der Typ erhält den Fokus, und sein Inhalt wird im Klassendetailsfenster angezeigt.  
  
2.  Klicken Sie im Fenster „Klassendetails“ in dem Abschnitt, der die zu erstellende Art von Member enthält, auf **\<Member hinzufügen>**. Wenn Sie z.B. ein Feld hinzufügen möchten, klicken Sie auf **\<Feld hinzufügen>**.  
  
3.  Geben Sie den Namen des zu erstellenden Members ein, und drücken Sie die EINGABETASTE.  
  
     Daraufhin wird eine neue Membersignatur erstellt und dem Typ hinzugefügt. Der Member ist nun im Code vorhanden und wird im **Klassen-Designer**, im Klassendetailsfenster und im Eigenschaftenfenster angezeigt.  
  
4.  Wahlweise können Sie weitere Memberdetails angeben, z. B. den Typ.  
  
     **Hinweis:** Sie können Member auch mithilfe von Tastenkombinationen erstellen. Weitere Informationen finden Sie unter [Tastenkombinationen und Mausaktionen im Klassendiagramm und Fenster „Klassendetails“ (Klassen-Designer)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md).  
  
##  <a name="ModifyTypeMembers"></a> Ändern von Typmembern  
 Mit dem Klassen-Designer können Sie die Member der Typen ändern, die im Diagramm angezeigt werden. Sie können die Member jedes nicht schreibgeschützten Typs ändern, die in einem Klassendiagramm angezeigt werden. (Weitere Informationen finden Sie unter [Anzeigen von schreibgeschützten Informationen (Klassen-Designer)](http://msdn.microsoft.com/en-us/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Ändern Sie Typmember, indem Sie die direkte Bearbeitung auf der Entwurfsoberfläche, das Eigenschaftenfenster und das Klassendetailsfenster verwenden.  
  
 Alle im Klassendetailsfenster angezeigten Member stellen die Member der Typen im Klassendiagramm dar. Es gibt vier Arten von Membern: Methoden, Eigenschaften, Felder und Ereignisse.  
  
 Alle Memberzeilen werden unter Überschriften anzeigt, mit denen die Member nach Typ gruppiert werden. So werden beispielsweise alle Eigenschaften unter der Überschrift **Eigenschaften** angezeigt. Diese kann als Knoten im Raster reduziert oder erweitert werden.  
  
 In jeder Memberzeile werden die folgenden Elemente angezeigt:  
  
-   **Membersymbol**  
  
     Jede Memberart wird mit einem besonderen Symbol dargestellt. Zeigen Sie mit der Maus auf das Membersymbol, um die Signatur des Members einzublenden. Klicken Sie auf das Membersymbol oder in den Leerraum links neben dem Membersymbol, um die Zeile auszuwählen.  
  
-   **Membername**  
  
     In der Spalte **Name** in einer Memberzeile wird der Name des Members angezeigt. Dieser Name wird auch im Eigenschaftenfenster in der Eigenschaft **Name** angezeigt. Verwenden Sie diese Zelle, um den Namen eines beliebigen nicht schreibgeschützten Members zu ändern.  
  
     Zeigen Sie mit dem Mauszeiger auf den Namen des Members, um ihn vollständig anzuzeigen, wenn die Spalte **Name** nicht breit genug ist.  
  
-   **Memberart**  
  
     In der Zelle **Membertyp** wird IntelliSense verwendet. Sie können daher einen Typ aus der Liste aller Typen auswählen, die im aktuellen Projekt oder in Projekten, auf die verwiesen wird, verfügbar sind.  
  
-   **Membermodifizierer**  
  
     Ändern Sie den Sichtbarkeitsmodifizierer eines Members in `Public` (`public`), `Private` (`private`), `Friend` (`internal`), `Protected` (`protected`), `Protected``Friend` (`protected``internal`) oder `Default`.  
  
-   **\<Member hinzufügen>**  
  
     Die letzte Zeile des Fensters „Klassendetails“ enthält in der Zelle **Name** den Text **\<Member hinzufügen>**. Wenn Sie auf diese Zelle klicken, können Sie einen neuen Member erstellen. Weitere Informationen finden Sie unter [Erstellen von Membern](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
-   **Membereigenschaften im Eigenschaftenfenster**  
  
     Im Klassendetailsfenster wird eine Teilmenge der im Eigenschaftenfenster angezeigten Membereigenschaften angezeigt. Nach einer Änderung einer Eigenschaft an einem Ort wird der Wert der Eigenschaft global aktualisiert. Dies bedeutet u. a., dass ihr Wert auch am anderen Ort angezeigt wird.  
  
-   **Zusammenfassung**  
  
     In der Zelle **Zusammenfassung** ist eine Zusammenfassung der Informationen zum Member verfügbar. Klicken Sie in der Zelle **Zusammenfassung** auf die Auslassungszeichen, um die Informationen **Zusammenfassung**, **Rückgabetyp** und **Hinweise** für den Member anzuzeigen und zu bearbeiten.  
  
-   **Ausblenden**  
  
     Wenn das Kontrollkästchen **Ausblenden** aktiviert ist, wird der Member im Typ nicht angezeigt.  
  
#### <a name="to-modify-a-type-member"></a>So ändern Sie einen Typmember  
  
1.  Wählen Sie mit dem Klassen-Designer einen Typ aus.  
  
2.  Wenn das Klassendetailsfenster nicht angezeigt wird, klicken Sie auf der Klassen-Designer-Symbolleiste auf die Schaltfläche **Klassendetailsfenster**.  
  
3.  Bearbeiten Sie die Werte in den Feldern des Rasters im Klassendetailsfenster. Drücken Sie nach jeder Änderung die EINGABETASTE, oder aktivieren Sie auf andere Weise ein anderes Feld, z. B. durch Drücken der TAB-TASTE. Die Änderungen sind im Code sofort sichtbar.  
  
    > [!NOTE]
    >  Wenn Sie nur den Namen eines Members ändern möchten, können Sie dafür die direkte Bearbeitung verwenden.  
  
##  <a name="AddMethodParams"></a> Hinzufügen von Parametern zu Methoden  
 Fügen Sie Methoden Parameter hinzu, indem Sie das Klassendetailsfenster verwenden. Parameter können als erforderlich oder optional konfiguriert werden. Wenn ein Wert für die Eigenschaft **Optional Default** angegeben wird, wird der Designer angewiesen, Code als optionalen Parameter zu generieren.  
  
 Parameterzeilen enthalten die folgenden Elemente:  
  
-   **Name**  
  
     In der Spalte **Name** in einer Parameterzeile wird der Name des Parameters angezeigt. Dieser Name wird auch im Eigenschaftenfenster in der Eigenschaft **Name** angezeigt. In dieser Zelle können Sie den Namen eines nicht schreibgeschützten Parameters ändern.  
  
     Zeigen Sie auf den Parameternamen, um ihn anzuzeigen, wenn die Spalte **Name** nicht breit genug ist, um den Namen vollständig anzuzeigen.  
  
-   **Type**  
  
     In der Zelle **Parametertyp** wird IntelliSense verwendet, d.h. Sie können einen Typ aus einer Liste aller im aktuellen Projekt oder in Projekten, auf die verwiesen wird, verfügbaren Typen auswählen.  
  
-   **Modifizierer**  
  
     In der Zelle **Modifizierer** in einer Parameterzeile kann ein neuer Modifizierer für den Parameter eingegeben und angezeigt werden. Wenn Sie einen neuen Parametermodifizierer eingeben möchten, verwenden Sie das Dropdown-Listenfeld, um in C# zwischen **None**, **ref**, **out** oder **params** und in VB zwischen **ByVal**, **ByRef** oder **ParamArray** zu wählen.  
  
-   **Zusammenfassung**  
  
     In der Zelle **Zusammenfassung** in einer Parameterzeile können Sie Codekommentare eingeben, die in IntelliSense angezeigt werden, wenn Sie den Parameter in den Code-Editor eingeben.  
  
-   **\<Parameter hinzufügen>**  
  
     Die letzte Parameterzeile eines Members enthält in der Zelle **Name** den Text **<add parameter>** (Parameter hinzufügen>). Klicken Sie in die Zelle, um einen neuen Parameter zu erstellen. Weitere Informationen finden Sie unter [So fügen Sie einer Methode einen Parameter hinzu](../ide/creating-and-configuring-type-members-class-designer.md#HowToAddParameterToMethod).  
  
 **Parametereigenschaften im Eigenschaftenfenster**  
  
 Im Eigenschaftenfenster werden die gleichen Parametereigenschaften wie im Klassendetailsfenster angezeigt: **Name**, **Type**, **Modifier**, **Summary** sowie **Optional Default**. Wenn Sie eine Eigenschaft in einem der beiden Fenster ändern, wird der Wert der Eigenschaft global aktualisiert, d. h. auch die Anzeige des zugehörigen Werts im jeweils anderen Fenster.  
  
> [!NOTE]
>  Informationen zum Hinzufügen eines Parameters zu einem Delegaten finden Sie unter [Erstellen von Membern](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
> [!NOTE]
>  Ein Destruktor ist zwar eine Methode, kann jedoch nicht über Parameter verfügen.  
  
###  <a name="HowToAddParameterToMethod"></a> So fügen Sie einer Methode einen Parameter hinzu  
  
1.  Klicken Sie auf der Diagrammoberfläche auf den Typ, der die Methode enthält, der Sie einen Parameter hinzufügen möchten.  
  
     Der Typ erhält den Fokus, und sein Inhalt wird im Klassendetailsfenster angezeigt.  
  
2.  Erweitern Sie im Klassendetailsfenster die Zeile der Methode, der Sie einen Parameter hinzufügen möchten.  
  
     Es wird eine eingerückte Parameterzeile angezeigt, die nur ein Klammernpaar und die Wörter **\<Parameter hinzufügen>** enthält.  
  
3.  Klicken Sie auf **\<Parameter hinzufügen>**, geben Sie den Namen des neuen Parameters ein, und drücken Sie die **EINGABETASTE**.  
  
     Der neue Parameter wird zur Methode und zum Code der Methode hinzugefügt. Er wird im Klassendetailsfenster und im Eigenschaftenfenster angezeigt.  
  
4.  Wahlweise können Sie weitere Parameterdetails angeben, z. B. den Typ.  
  
### <a name="to-add-an-optional-parameter-to-a-method"></a>So fügen Sie einer Methode einen optionalen Parameter hinzu  
  
1.  Klicken Sie auf der Diagrammoberfläche auf den Typ, der die Methode enthält, der Sie einen optionalen Parameter hinzufügen möchten.  
  
     Der Typ erhält den Fokus, und sein Inhalt wird im Klassendetailsfenster angezeigt.  
  
2.  Erweitern Sie im Klassendetailsfenster die Zeile der Methode, der Sie einen optionalen Parameter hinzufügen möchten.  
  
     Es wird eine eingerückte Parameterzeile angezeigt, die nur ein Klammernpaar und die Wörter **\<Parameter hinzufügen>** enthält.  
  
3.  Klicken Sie auf **\<Parameter hinzufügen>**, geben Sie den Namen des neuen Parameters ein, und drücken Sie die **EINGABETASTE**.  
  
     Der neue Parameter wird zur Methode und zum Code der Methode hinzugefügt. Er wird im Klassendetailsfenster und im Eigenschaftenfenster angezeigt.  
  
4.  Geben Sie im Eigenschaftenfenster einen Wert für die Eigenschaft **Optional Default** ein. Wenn Sie die "Optional Default"-Eigenschaft eines Parameters festlegen, wird dieser Parameter optional.  
  
    > [!NOTE]
    >  Optionale Parameter müssen in der Parameterliste die letzten Parameter sein.  
  
##  <a name="ClassDetailsUsageNotes"></a> Hinweise zur Verwendung von Klassendetails  
 Beachten Sie die folgenden Tipps zur Verwendung des Klassendetailsfensters.  
  
 **Bearbeitbare und nicht bearbeitbare Zellen**  
  
 Alle Zellen im Klassendetailsfenster sind bis auf einige Ausnahmen bearbeitbar:  
  
-   Der gesamte Typ ist schreibgeschützt, wenn er sich beispielsweise in einer Assembly befindet, auf die verwiesen wird (weitere Informationen finden Sie unter [Anzeige von schreibgeschützten Informationen (Klassen-Designer)](http://msdn.microsoft.com/en-us/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Wenn Sie die Form im Klassen-Designer auswählen, werden die entsprechenden Details im Klassendetailsfenster schreibgeschützt angezeigt.  
  
-   Für Indexer ist der Name schreibgeschützt, der Rest (Typ, Modifizierer, Zusammenfassung) ist jedoch bearbeitbar.  
  
-   Alle Generika weisen im Klassendetailsfenster schreibgeschützte Parameter auf. Um einen generischen Parameter zu ändern, bearbeiten Sie den entsprechenden Quellcode.  
  
-   Der Name des für einen generischen Typ definierten Typparameters ist schreibgeschützt.  
  
-   Wenn der Code eines Typs fehlerhaft (nicht analysierbar) ist, wird der Inhalt des Typs im Klassendetailsfenster schreibgeschützt angezeigt.  
  
 **Klassendetailsfenster und Quellcode**  
  
-   Klicken Sie zum Anzeigen von Quellcode im Klassendetailsfenster (oder im Klassen-Designer) mit der rechten Maustaste auf eine Form, und klicken Sie anschließend auf Code anzeigen. Die Quellcodedatei wird geöffnet, und es wird ein Bildlauf zum ausgewählten Element durchgeführt.  
  
-   Jede Änderung des Quellcodes wird sofort durch die Anzeige von Signaturinformationen im Klassen-Designer und im Klassendetailsfenster sichtbar. Falls das Klassendetailsfenster zu diesem Zeitpunkt geschlossen ist, werden die neuen Informationen beim nächsten Öffnen des Fensters sichtbar.  
  
-   Wenn der Code eines Typs fehlerhaft (nicht analysierbar) ist, wird der Inhalt des Typs im Klassendetailsfenster schreibgeschützt angezeigt.  
  
 **Zwischenablagefunktionalität im Klassendetailsfenster**  
  
 Sie können Felder oder Zeilen im Klassendetailsfenster kopieren oder ausschneiden und in einen anderen Typ einfügen. Es können nur Zeilen ausgeschnitten werden, die nicht schreibgeschützt sind. Wenn Sie die Zeile einfügen, wird zur Vermeidung eines Konflikts im Klassendetailsfenster ein neuer (vom Namen der kopierten Zeile abgeleiteter) Name zugewiesen.  
  
##  <a name="ReadOnlyInfo"></a> Anzeigen von schreibgeschützten Informationen  
 Im Klassen-Designer und im Klassendetailsfenster können die Typen (und Member der Typen) für folgende Elemente angezeigt werden:  
  
-   ein Projekt, das ein Klassendiagramm enthält  
  
-   ein Projekt, auf das von einem Projekt verwiesen wird, das ein Klassendiagramm enthält  
  
-   eine Assembly, auf die von einem Projekt verwiesen wird, das ein Klassendiagramm enthält  
  
 In den beiden letzten Fällen ist die Entität (ein Typ oder Member), auf die verwiesen wird, im entsprechenden Klassendiagramm schreibgeschützt.  
  
 Ein gesamtes Projekt oder Projektteile, z. B. einzelne Dateien, können schreibgeschützt sein. Ein Projekt oder eine zugehörige Datei ist in der Regel dann schreibgeschützt, wenn die Quellcodeverwaltung verwendet wird (und das Projekt nicht ausgecheckt wurde), das Projekt oder die Datei in einer externen Assembly enthalten ist oder das Betriebssystem die Dateien als schreibgeschützt festlegt.  
  
 **Quellcodeverwaltung**  
  
 Da ein Klassendiagramm in einem Projekt als Datei gespeichert wird, müssen Sie das Projekt auschecken, damit im Klassen-Designer oder Klassendetailsfenster vorgenommene Änderungen übernommen werden.  
  
 **Schreibgeschützte Projekte**  
  
 Das Projekt ist möglicherweise nicht aufgrund der Quellcodeverwaltung, sondern aus einem anderen Grund schreibgeschützt. Wenn Sie das Projekt schließen, wird ein Dialogfeld mit der Frage angezeigt, ob die Projektdatei überschrieben werden soll, Änderungen verworfen werden sollen oder der Vorgang abgebrochen werden soll. Wenn Sie festlegen, dass die Projektdatei überschrieben werden soll, werden die Projektdateien überschrieben und mit Lese- und Schreibzugriff versehen. Die neue Klassendiagrammdatei wird hinzugefügt.  
  
 **Schreibgeschützte Typen**  
  
 Wenn Sie versuchen, ein Projekt zu speichern, das einen Typ enthält, dessen Quellcodedatei schreibgeschützt ist, wird das Dialogfeld **Schreibgeschützte Datei speichern** angezeigt. Hier haben Sie die Möglichkeit, die Datei unter einem neuen Namen und/oder an einem neuen Speicherort zu speichern oder die schreibgeschützte Datei zu überschreiben. Wenn Sie die Datei überschreiben, ist die Datei nicht mehr schreibgeschützt.  
  
 Weist eine Codedatei einen Syntaxfehler auf, werden die Formen, die den Code in der Datei anzeigen, so lange mit Schreibschutz versehen, bis der Syntaxfehler behoben wird. Formen in diesem Zustand zeigen roten Text und ein rotes Symbol mit der Quickinfo "Die Quellcodedatei enthält einen Analysefehler" an.  
  
 Ein Typ, auf den verwiesen wird (z. B. ein .NET Framework-Typ) und der unter einem anderen Projektknoten oder unter dem Knoten einer Assembly, auf die verwiesen wird, vorhanden ist, wird auf der Entwurfsoberfläche des Klassen-Designers als schreibgeschützt angezeigt. Ein lokaler Typ im geöffneten Projekt ist mit Lese- und Schreibzugriff versehen, und seine Form wird auf der Entwurfsoberfläche des Klassen-Designers entsprechend angegeben.  
  
 Indexer sind in Code und im Klassendetailsfenster mit Lese- und Schreibzugriff versehen, der Indexername hingegen ist schreibgeschützt.  
  
 Partielle Methoden können nicht mithilfe des Klassen-Designers oder des Klassendetailsfensters bearbeitet werden. Verwenden Sie dazu den Code-Editor.  
  
 Systemeigener C++-Code kann nicht mithilfe des Klassen-Designers oder des Klassendetailsfensters bearbeitet werden. Verwenden Sie dazu den Code-Editor.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Anzeigen von Typen und Beziehungen (Klassen-Designer)](../ide/viewing-types-and-relationships-class-designer.md)|Sie können die vorhandenen Typen, Member und Beziehungen in einem Klassendiagramm anzeigen.|  
|[Refactoring von Klassen und Typen (Klassen-Designer)](../ide/refactoring-classes-and-types-class-designer.md)|Mithilfe des Refactorings können Sie Typen und Typmember einfach umbenennen. Sie können Member auch zwischen Klassen verschieben, eine Klasse in partielle Klassen aufteilen und Schnittstellen implementieren.|