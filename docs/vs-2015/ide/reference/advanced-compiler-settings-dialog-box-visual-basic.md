---
title: Dialogfeld „Erweiterte Compilereinstellungen“ (Visual Basic) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 52
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba666b0ff5544b185f82a66c78d6259e9f1268fd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651768"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Dialogfeld "Erweiterte Compilereinstellungen (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie das Dialogfeld **Erweiterte Compilereinstellungen** des **Projekt-Designers**, um die erweiterten Buildkonfigurationseigenschaften des Projekts anzugeben. Dieses Dialogfeld gilt nur für Visual Basic-Projekte.

### <a name="to-access-this-dialog-box"></a>So öffnen Sie das Dialogfeld

1. Wählen Sie im **Projektmappen-Explorer** einen Projektknoten (nicht den Knoten **Projektmappe**) aus.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Kompilieren**.

3. Wählen Sie auf der Seite [„Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) die **Konfiguration** und **Plattform** aus. In vereinfachten Buildkonfigurationen werden die Listen **Konfiguration** und **Plattform** nicht angezeigt. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

4. Klicken Sie auf **Erweiterte Kompilierungsoptionen**.

   [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="optimizations"></a>Optimierungen
 Die folgenden Optionen geben Optimierungen an, die in einigen Fällen eine Programmdatei verkleinern kann, dazu führen, dass ein Programm schneller ausgeführt wird oder den Buildprozess beschleunigen können.

 **Ganzzahlige Überlauf Überprüfungen entfernen** Standardmäßig ist dieses Kontrollkästchen deaktiviert, um eine ganzzahlige Überlauf Überprüfung zu aktivieren. Aktivieren Sie dieses Kontrollkästchen, um die Überprüfungen auf Ganzzahlüberlauf zu entfernen. Wenn Sie dieses Kontrollkästchen aktivieren, werden Integerberechnungen möglicherweise beschleunigt. Wenn Sie jedoch die Überprüfung auf Überlauf und Datentypkapazitäten entfernen, werden womöglich falsche Ergebnisse gespeichert, ohne dass ein Fehler ausgelöst wird.

 Wenn Überlaufbedingungen überprüft werden und eine ganzzahlige Operation überläuft, wird eine <xref:System.OverflowException>-Ausnahme ausgegeben. Wenn Überlaufbedingungen nicht aktiviert werden, lösen Überprüfungen auf Ganzzahlüberlauf keine Ausnahme aus.

 **Optimierungen aktivieren** Standardmäßig ist dieses Kontrollkästchen deaktiviert, um Compileroptimierungen zu deaktivieren. Aktivieren Sie dieses Kontrollkästchen, um Compileroptimierungen zu aktivieren. Durch Compileroptimierungen wird Ihre Ausgabedatei kleiner, schneller und effizienter. Da Optimierungen jedoch zu Neuanordnung von Code in der Ausgabedatei führen können, können Compileroptimierungen das Debuggen erschweren.

 **DLL-Basisadresse** Dieses Textfeld zeigt die Standard-DLL-Basisadresse im Hexadezimal Format an. Sie können dieses Textfeld in Klassenbibliotheks- und Steuerelementbibliotheksprojekten verwenden, um die Basisadresse anzugeben, die verwendet werden soll, wenn die DLL erstellt wird.

 **Debuginformationen generieren** Wählen Sie in der Liste **keine**, **vollständig**oder **nur PDB** aus. **None** (Keine) gibt an, das keine Informationen zum Debuggen generiert werden. **Full** (Vollständig) gibt an, dass vollständige Debuginformationen generiert werden. **pdb-only** (nur pdb) gibt an, dass nur PDB-Debuginformationen generiert werden. Standardmäßig ist der Wert **Full** festgelegt.

## <a name="compilation-constants"></a>Kompilierungskonstanten
 Bedingte Kompilierungskonstanten haben einen ähnlichen Effekt wie das Verwenden einer [#Const](https://msdn.microsoft.com/library/707669e5-23f9-4f17-8622-a0d534429386)-Präprozessoranweisung in einer Quelldatei, außer dass Konstanten öffentlich sind und für alle Dateien im Projekt gelten. Sie können die bedingten Kompilierungskonstanten zusammen mit der Direktive [#If...Then...#Else](https://msdn.microsoft.com/library/10bba104-e3fd-451b-b672-faa472530502) verwenden, um Quelldateien bedingt zu kompilieren. Weitere Informationen finden Sie unter [Bedingte Kompilierung](https://msdn.microsoft.com/library/9c35e55e-7eee-44fb-a586-dad1f1884848).

 **Debug-Konstante definieren** Standardmäßig ist dieses Kontrollkästchen aktiviert und gibt an, dass eine debugabkonstante festgelegt wird.

 Ablauf **Verfolgungs Konstante definieren** Standardmäßig ist dieses Kontrollkästchen aktiviert und gibt an, dass eine Ablauf Verfolgungs Konstante festgelegt wird.

 **Benutzerdefinierte Konstanten** Geben Sie in diesem Textfeld benutzerdefinierte Konstanten für die Anwendung ein. Die Einträge müssen durch Kommas getrennt sein und folgendes Format vorweisen: **Name1="Wert1",Name2="Wert2",Name3="Wert3"**

## <a name="other-settings"></a>Weitere Einstellungen
 **Serialisierungsassemblys generieren** Mit dieser Einstellung wird angegeben, ob der Compiler XML-Serialisierungsassemblys erstellt. Serialisierungsassemblys können die Startleistung von <xref:System.Xml.Serialization.XmlSerializer> verbessern, sofern Sie diese Klasse zum Serialisieren von Typen im Code verwendet haben. Standardmäßig ist diese Option auf **Auto** festgelegt, d.h., es werden nur dann Serialisierungsassemblys generiert, wenn Sie <xref:System.Xml.Serialization.XmlSerializer> verwendet haben, um Typen im Code in XML zu codieren. **Aus** gibt an, dass grundsätzlich keine Serialisierungsassemblys generiert werden, unabhängig davon, ob im Code <xref:System.Xml.Serialization.XmlSerializer> verwendet wird. **Ein** gibt an, dass immer Serialisierungsassemblys generiert werden. Serialisierungsassemblys tragen den Namen `TypeName`.XmlSerializers.dll.

## <a name="see-also"></a>Siehe auch
 [Seite „Kompilieren“, Projekt-Designer (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
