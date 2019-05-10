---
title: Refactoring von Klassen und Typen (Klassen-Designer) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eaee3dae25f5f2e5544a2521a7bce0201b45a3e2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441153"
---
# <a name="refactoring-classes-and-types-class-designer"></a>Refactoring von Klassen und Typen (Klassen-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie einen Code umgestalten, ist er leichter zu verstehen, zu verwalten und effizienter durch die Änderung seiner internen Struktur und die Art, wie seine Objekte entworfen werden, nicht aber sein externes Verhalten. Verwenden Sie den Klassen-Designer und im Klassendetail-Fenster, um die Arbeit, die Sie erledigen müssen, und die Wahrscheinlichkeit der Einführung von Fehlern beim Umgestalten von Visual C# .NET, Visual Basic .NET oder C++-Code im Visual Studio-Projekt  zu reduzieren.  
  
> [!NOTE]
> Die Dateien eines Projekts sind möglicherweise schreibgeschützt, da das Projekt unter Quellcodeverwaltung steht und nicht ist ausgecheckt ist; auf das Projekt verwiesen wird oder die Dateien auf dem Datenträger als schreibgeschützt markiert sind. Bei der Arbeit an einem Projekt in einem dieser Zustände werden verschiedene Möglichkeiten zum Speichern Ihrer Arbeit je nach Zustand des Projekts angezeigt. Dies gilt für die Umgestaltung eines Codes und für einen Code, den Sie auf andere Weise ändern, z. B. indem Sie ihn direkt bearbeiten. Weitere Informationen finden Sie unter [Anzeige schreibgeschützter Informationen (Klassen-Designer)](http://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Unterstützender Inhalt|  
|----------|------------------------|  
|**Refactoring von Klassen:** Sie können Refactoringvorgänge zum Aufteilen einer Klasse in partielle Klassen oder zur Implementierung einer abstrakten Klasse verwenden.|-   [Vorgehensweise: Aufteilen einer Klasse in partielle Klassen im Klassen-Designer](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|  
|**Arbeiten mit Schnittstellen:** In Klassen-Designer können Sie eine Schnittstelle im Klassendiagramm implementieren, indem Sie sie mit einer Klasse verbinden, die Code für die Schnittstellenmethoden bereitstellt.|-   [Vorgehensweise: Implementieren einer Schnittstelle im Klassen-Designer](../ide/how-to-implement-an-interface-class-designer.md)|  
|**Refactoring von Typen, Typmembern und Parametern:** Über den Klassen-Designer können Sie Typen umbenennen, Typmember überschreiben oder Typmember aus einem Typ in einen anderen verschieben. Außerdem können Sie Nullable-Typen erstellen.|-   [Umbenennen von Typen und Typmembern](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [Verschieben von Typmembern von einem Typ in einen anderen](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers)<br />-   [Vorgehensweise: Erstellen eines Typs im Klassen-Designer, der NULL-Werte zulässt](../ide/how-to-create-a-nullable-type-class-designer.md)|  
  
### <a name="RenamingTypesAndMembers"></a>Umbenennen von Typen und Typmembern  
 Im Klassen-Designer können Sie einen Typ oder einen Member eines Typs im Klassendiagramm oder im Eigenschaftenfenster umbenennen. Im Fenster Klassendetails können Sie den Namen eines Members, aber keinen Typ ändern. Die Umbenennung eines Typs oder Typmember wird an alle Fenster und Codepositionen übergeben, in denen der alte Name auftrat.  
  
##### <a name="to-rename-a-name-in-the-class-designer"></a>Um einen Namen im Klassen-Designer umzubenennen,  
  
1. Wählen Sie im Klassendiagramm den Typ oder Member aus, und klicken Sie auf den Namen.  
  
     Der Name des Members kann jetzt bearbeitet werden.  
  
2. Geben Sie den neuen Namen für den Typ oder Typmember ein  
  
##### <a name="to-rename-a-name-in-the-class-details-window"></a>Um einen Namen im Fenster Klassendetails umzubenennen,  
  
1. Um das Fenster Klassendetails anzuzeigen, klicken Sie mit der rechten Maustaste auf den Typ oder den Typmember und dann auf **Klassendetails**.  
  
     Das Fenster Klassendetails wird angezeigt.  
  
2. Ändern Sie in der Spalte **Name** den Namen des Typmembers.  
  
3. Um den Fokus von der Zelle zu verschieben, drücken Sie die **EINGABETASTE** , oder klicken Sie außerhalb der Zelle.  
  
    > [!NOTE]
    > Im Fenster Klassendetails können Sie den Namen eines Members, aber keinen Typ ändern.  
  
##### <a name="to-rename-a-name-in-the-properties-window"></a>Um einen Namen im Eigenschaftenfenster zu ändern  
  
1. Rechtsklicken Sie im Klassendiagramm oder im Fenster Klassendetails  auf Typ oder Member und klicken Sie dann auf **Eigenschaften**.  
  
     Das Fenster Eigenschaften wird angezeigt und zeigt die Eigenschaften für den Typ oder Typmember an.  
  
2. In der Eigenschaft **Name** ändern Sie den Namen des Typs bzw. Typmembers.  
  
     Der neue Name wird an alle Fenster und Codepositionen im aktuellen Projekt übertragen, in dem der alte Name auftrat.  
  
### <a name="MovingTypeMembers"></a> Typmember von einem Typ in einen anderen verschieben  
 Mit dem **Klassen-Designer**können Sie einen Typmember von einem Typ in einen anderen Typ verschieben, wenn beide Typen im aktuellen Klassendiagramm sichtbar sind.  
  
##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Um einen Typmember von einem Typ in einen anderen zu verschieben.  
  
1. Rechtsklicken Sie in einem Typ, der auf der Entwurfsoberfläche angezeigt wird, auf den Member, den Sie in einen anderen Typ verschieben möchten, und klicken Sie dann auf **Aussschneiden**.  
  
2. Rechtsklicken Sie auf den Zieltyp und klicken Sie dann auf **Einfügen**.  
  
     Die Eigenschaft wird aus dem Quelltyp entfernt und im Zieltyp angezeigt wird.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Anzeigen von Typen und Beziehungen (Klassen-Designer)](../ide/viewing-types-and-relationships-class-designer.md)||  
|[Entwerfen von Klassen und Typen (Klassen-Designer)](../ide/designing-classes-and-types-class-designer.md)||
