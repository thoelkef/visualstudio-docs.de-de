---
title: Binden von Windows Forms-Steuerelementen an Daten
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8a03f4df57b216fa68e5ac24df80b67917aa3e3f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672990"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Binden von Windows Forms-Steuerelementen an Daten in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an Windows Forms binden. Zum Erstellen dieser Daten gebundenen Steuerelemente können Sie Elemente aus dem Fenster **Datenquellen** auf die Windows Forms-Designer in Visual Studio ziehen. In diesem Thema werden einige der häufigsten Aufgaben, Tools und Klassen beschrieben, die beim Erstellen von datengebundenen Anwendungen verwendet werden.

 ![Datenquellen-Zieh Vorgang](../data-tools/media/raddata-data-source-drag-operation.png "Drag-Vorgang der raddata-Datenquelle")

 Allgemeine Informationen zum Erstellen von Daten gebundenen Steuerelementen in Visual Studio finden Sie unterbinden von Steuer [Elementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Weitere Informationen zur Datenbindung in Windows Forms finden Sie unter [Windows Forms Datenbindung](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa).

## <a name="in-this-section"></a>In diesem Abschnitt

- [Binden von Windows Forms-Steuerelementen an Daten](../data-tools/bind-windows-forms-controls-to-data.md)

- [Ausführen eines Commits für aktuelle Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)

- [Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen](../data-tools/create-lookup-tables-in-windows-forms-applications.md)

- [Erstellen eines Windows Forms zum Suchen von Daten](../data-tools/create-a-windows-form-to-search-data.md)

- [Erstellen eines Windows Forms-Benutzersteuerelements, das die einfache Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)

- [Erstellen eines Windows Forms-Benutzersteuerelements, das komplexe Datenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)

- [Erstellen eines Windows Forms-Benutzersteuerelements, das Nachschlagedatenbindung unterstützt](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

- [Übergeben von Daten zwischen Formularen](../data-tools/pass-data-between-forms.md)

## <a name="bindingsource-component"></a>BindingSource-Komponente
 Die <xref:System.Windows.Forms.BindingSource>-Komponente dient zwei Zwecken. Erstens stellt sie eine Abstraktionsebene bereit, wenn die Steuerelemente auf dem Formular an Daten gebunden werden. Steuerelemente auf dem Formular werden an die <xref:System.Windows.Forms.BindingSource>-Komponente gebunden (also nicht direkt an eine Datenquelle).

 Zweitens kann so eine Auflistung von Objekten verwaltet werden. Wenn Sie zur <xref:System.Windows.Forms.BindingSource>-Komponente einen Typ hinzuzufügen, wird eine Liste dieses Typs erstellt.

 Weitere Informationen über die <xref:System.Windows.Forms.BindingSource>-Komponente finden Sie unter:

- [BindingSource-Komponente](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9)

- [Übersicht über die BindingSource-Komponente](https://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)

- [Architektur der BindingSource-Komponente](https://msdn.microsoft.com/library/7bc69c90-8a11-48b1-9336-3adab5b41591)

## <a name="bindingnavigator-control"></a>BindingNavigator-Steuerelement
 Diese Komponente stellt eine Benutzeroberfläche zum Navigieren durch Daten bereit, die von einer Windows-Anwendung angezeigt werden. Weitere Informationen finden Sie unter [BindingNavigator-Steuerelement](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

## <a name="datagridview-control"></a>DataGridView-Steuerelement
 Verwenden Sie das <xref:System.Windows.Forms.DataGridView>-Steuerelement, um tabellarische Daten aus vielen unterschiedlichen Arten von Datenquellen anzuzeigen und zu bearbeiten. Sie können Daten mit der <xref:System.Windows.Forms.DataGridView>-Eigenschaft an ein <xref:System.Windows.Forms.DataGridView.DataSource%2A>-Element binden. Weitere Informationen finden Sie unter [Übersicht über das DataGridView-Steuer](https://msdn.microsoft.com/library/0a45c661-89dc-4390-9cc6-c47eee501488)Element.

## <a name="see-also"></a>Siehe auch
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
