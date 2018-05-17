---
title: Refactoring von Klassen und Typen (Klassen-Designer)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3104266e92bc05f82a4d97fb62fc20bc9e79c0eb
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="refactoring-classes-and-types-class-designer"></a>Refactoring von Klassen und Typen (Klassen-Designer)

Wenn Sie einen Code umgestalten, ist er leichter zu verstehen, zu verwalten und effizienter durch die Änderung seiner internen Struktur und die Art, wie seine Objekte entworfen werden, nicht aber sein externes Verhalten. Verwenden Sie den Klassen-Designer und im Klassendetailsfenster, um die durchzuführenden Aufgaben und die Wahrscheinlichkeit der Einführung von Fehlern beim Umgestalten von C#-, Visual Basic- oder C++-Code im Visual Studio-Projekt zu reduzieren.

> [!NOTE]
> Die Dateien eines Projekts sind möglicherweise schreibgeschützt, da das Projekt unter Quellcodeverwaltung steht und nicht ausgecheckt ist, auf das Projekt verwiesen wird oder die Dateien auf dem Datenträger als schreibgeschützt markiert sind. Bei der Arbeit an einem Projekt in einem dieser Zustände werden verschiedene Möglichkeiten zum Speichern Ihrer Arbeit je nach Zustand des Projekts angezeigt. Dies gilt für die Umgestaltung eines Codes und für einen Code, den Sie auf andere Weise ändern, z. B. indem Sie ihn direkt bearbeiten.

## <a name="common-tasks"></a>Allgemeine Aufgaben

|Aufgabe|Unterstützender Inhalt|
|----------|------------------------|
|**Umgestaltung von Klassen:** Sie können Umgestaltungsvorgänge zum Aufteilen eine Klasse in Teilklassen oder zur Implementierung einer abstrakten Klasse verwenden.|-   [Vorgehensweise: Aufteilen einer Klasse in partielle Klassen (Klassen-Designer)](how-to-split-a-class-into-partial-classes.md)|
|**Arbeiten mit Schnittstellen:** Im Klassen-Designer Sie können eine Schnittstelle im Klassendiagramm implementieren, indem Sie es an eine Klasse anhängen, die einen Code für die Schnittstellenmethoden vorsieht.|-   [How to: Implement an Interface (Class Designer) (Vorgehensweise: Implementieren einer Schnittstelle (Klassen-Designer))](how-to-implement-an-interface.md)|
|**Umgestaltung von Typen, Typmembern und Parametern:** Über den Klassen-Designer können Sie Typen umbenennen, Typmember überschreiben oder Typmember aus einem Typ in einen anderen verschieben. Außerdem können Sie Nullable-Typen erstellen.|-   [Umbenennen von Typen und Typmembern](refactoring-classes-and-types.md#rename)<br />-   [Verschieben von Typmembern von einem Typ in einen anderen](refactoring-classes-and-types.md#move)<br />-   [How to: Create a Nullable Type (Class Designer) (Vorgehensweise: Erstellen eines Nullable-Typs (Klassen-Designer))](how-to-create-a-nullable-type.md)|

<a name="rename"></a>
### <a name="rename-types-and-type-members"></a>Umbenennen von Typen und Typmembern

Im Klassen-Designer können Sie einen Typ oder einen Member eines Typs im Klassendiagramm oder im Eigenschaftenfenster umbenennen. Im Fenster Klassendetails können Sie den Namen eines Members, aber keinen Typ ändern. Die Umbenennung eines Typs oder Typmember wird an alle Fenster und Codepositionen übergeben, in denen der alte Name auftrat.

#### <a name="to-rename-a-name-in-the-class-designer"></a>Um einen Namen im Klassen-Designer umzubenennen,

1.  Wählen Sie im Klassendiagramm den Typ oder Member aus, und klicken Sie auf den Namen.

     Der Name des Members kann jetzt bearbeitet werden.

2.  Geben Sie den neuen Namen für den Typ oder Typmember ein

#### <a name="to-rename-a-name-in-the-class-details-window"></a>Ändern eines Namens im Fenster „Klassendetails“

1.  Um das Fenster Klassendetails anzuzeigen, klicken Sie mit der rechten Maustaste auf den Typ oder den Typmember und dann auf **Klassendetails**.

     Das Fenster Klassendetails wird angezeigt.

2.  Ändern Sie in der Spalte **Name** den Namen des Typmembers.

3.  Um den Fokus von der Zelle zu verschieben, drücken Sie die **EINGABETASTE** , oder klicken Sie außerhalb der Zelle.

    > [!NOTE]
    > Im Fenster Klassendetails können Sie den Namen eines Members, aber keinen Typ ändern.

#### <a name="to-rename-a-name-in-the-properties-window"></a>Um einen Namen im Eigenschaftenfenster zu ändern

1.  Rechtsklicken Sie im Klassendiagramm oder im Fenster Klassendetails  auf Typ oder Member und klicken Sie dann auf **Eigenschaften**.

     Das Fenster Eigenschaften wird angezeigt und zeigt die Eigenschaften für den Typ oder Typmember an.

2.  In der Eigenschaft **Name** ändern Sie den Namen des Typs bzw. Typmembers.

     Der neue Name wird an alle Fenster und Codepositionen im aktuellen Projekt übertragen, in dem der alte Name auftrat.

<a name="move"></a>
### <a name="move-type-members-from-one-type-to-another"></a>Verschieben von Typmembern von einem Typ in einen anderen

Mit dem **Klassen-Designer**können Sie einen Typmember von einem Typ in einen anderen Typ verschieben, wenn beide Typen im aktuellen Klassendiagramm sichtbar sind.

1.  Rechtsklicken Sie in einem Typ, der auf der Entwurfsoberfläche angezeigt wird, auf den Member, den Sie in einen anderen Typ verschieben möchten, und klicken Sie dann auf **Aussschneiden**.

2.  Rechtsklicken Sie auf den Zieltyp und klicken Sie dann auf **Einfügen**.

     Die Eigenschaft wird aus dem Quelltyp entfernt und im Zieltyp angezeigt wird.

## <a name="see-also"></a>Siehe auch

- [Anzeigen von Typen und Beziehungen](viewing-types-and-relationships.md)
- [Entwerfen von Klassen und Typen](designing-classes-and-types.md)