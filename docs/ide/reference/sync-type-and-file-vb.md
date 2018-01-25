---
title: Synchronisieren eines Typ und Dateinamens in Visual Basic | Microsoft-Dokumentation
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 93e1b1f446dc330b2c2c1c1e5b36e6a21e64f521
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-visual-basic"></a>Synchronisieren eines Typs mit einem Dateinamen oder eines Dateinamens mit einem Typ in Visual Basic

<!-- VERSIONLESS -->
**Dieses Feature ist in Visual Studio 2017 und höher verfügbar.  Darüber hinaus werden für ein derartiges Refactoring noch keine .NET Standard-Projekte unterstützt.**

**Beschreibung**: Hiermit können Sie einen Typ entsprechend des Dateinamens umbenennen oder einen Dateinamen entsprechend des darin enthaltenen Typs umbenennen.

**Hintergrund**: Sie haben eine Datei oder einen Typ umbenannt und noch nicht die entsprechende Datei oder den entsprechenden Typ aktualisiert. 

**Vorteile**: Das Platzieren eines Typs in eine Datei mit einem anderen Namen oder umgekehrt erschwert die Suche nach den gewünschten Elementen.  Durch das Umbenennen des Typs oder des Dateinamens wird der Code besser lesbar und einfacher zu navigieren.

**Vorgehensweise**:

1. Markieren Sie den Namen des zu synchronisierenden Typs, oder platzieren Sie den Textcursor in den Namen:

   ![Markierter Code](media/synctype-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen. Wählen Sie dann im Popupvorschaufenster die Option **Datei in *TypeName*.vb umbenennen** aus, wobei *TypeName* für den Namen des ausgewählten Typs steht.
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen. Wählen Sie dann im Popupvorschaufenster die Option **Typ in _Filename_ umbenennen** aus, wobei *Filename* für den Namen der aktuellen Datei steht.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus. Wählen Sie dann im Popupvorschaufenster die Option **Datei in *TypeName*.vb umbenennen** aus, wobei *TypeName* für den Namen des ausgewählten Typs steht.
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus. Wählen Sie dann im Popupvorschaufenster die Option **Typ in _Filename_ umbenennen** aus, wobei *Filename* für den Namen der aktuellen Datei steht.

   Der Typ oder die Datei wird sofort umbenannt.  Im nachfolgenden Beispiel wurde die Datei **Employee.vb** entsprechend des Typnamens in **Person.vb** umbenannt.

   ![Ergebnis des Inlinevorgangs](media/synctype-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)
