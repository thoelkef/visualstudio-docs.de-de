---
title: "VSCT-Beispiele in C# und C++ | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT-Dateien, Beispiele"
ms.assetid: 3218584b-c619-487c-9486-514b04937020
caps.latest.revision: 6
caps.handback.revision: 6
manager: "douge"
---
# VSCT-Beispiele in C# und C++
VSCT ist die neue Methode des Definieren von Befehlen geworden.  Dies ist eine Änderung vorgenommen, wie in der VSCT\-Beispiele in C\# und C\+\+ kompiliert werden.  Befehle werden jetzt in C\+\+ und C\# mit externen Dateien mit einem Symbol im Abschnitt der .vsct\-Datei definiert.  
  
## Befehle definieren  
  
### Externe Dateien C\+\+  
 In den C\+\+\-Beispielen schließt der VSCT\-Compiler externe Dateien, um die Konstanten zu definieren, die in den Definitionen der Befehle verwendet werden.  Die Möglichkeit, diese Dateien einzuschließen und Konstanten in Definitionen der Befehle darin zu definieren, ist ein `Extern`\-Tag innerhalb der .vsct\-Datei hinzuzufügen und den Namen der `href` Externe Dateiverweise innerhalb des Attributs anzugeben.  Diese Dateien sind:  
  
-   Guids.h  
  
-   CommandIDs.h  
  
-   Resources.h  
  
 Der folgende Ausschnitt aus einer C\+\+\-Datei .vsct wird veranschaulicht, wie diese Dateien einschließt:  
  
 `<!--This is the file with the definition of the Guids specific for this sample.-->`  
  
 `<Extern href="Guids.h"/>`  
  
 `<!--Definition of the IDs of the commands and VSCT elements specific for this sample.-->`  
  
 `<Extern href="CommandIds.h"/>`  
  
 `<!--Definition of the resources exposed by this package.  Here it is used for the ID of the bitmap.-->`  
  
 `<Extern href="Resource.h"/>`  
  
### C\#\-Symbole  
 In den C\#\-Beispielen hat die .vsct\-Datei `Symbols` einen Abschnitt in der Datei selbst, um Befehle zu definieren.  Die Definition von Symbolen in einer .vsct\-Datei in C\# stammt die Methode ab, die die ID der Elemente nach dem Befehl Tabelle definiert ist.  Im Folgenden wird ein Ausschnitt aus der Datei C\# .vsct, die die Befehle und Konstanten angibt, die ihnen zugeordneten:  
  
 `<Symbols>`  
  
 `<!--The first GUID defined here is the one for the package.  It does not contain numeric IDs.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsPkg" value="{746D5114-B030-4D64-9A6D-E2ABE1E78E56}" />`  
  
 `<!--The GUID for the command set is the one that contains the numeric IDs used in this sample`  
  
 `with the only exception of the one used for the bitmap.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsCmdSet" value="{10A79DAE-B33C-4FDB-8922-B056628858A1}">`  
  
 `<!--Menus-->`  
  
 `<IDSymbol name="MyToolbar" value="0x101" />`  
  
 `<!--Groups-->`  
  
 `<IDSymbol name="MyMenuGroup" value="0x1010" />`  
  
 `<IDSymbol name="MyToolbarGroup" value="0x1011" />`  
  
 `<IDSymbol name="MyMainToolbarGroup" value="0x1012" />`  
  
 `<IDSymbol name="MyEditorCtxGroup" value="0x1013" />`  
  
 `<!--Commands-->`  
  
 `<IDSymbol name="cmdidMyCommand" value="0x2001" />`  
  
 `<IDSymbol name="cmdidMyGraph" value="0x2002" />`  
  
 `<IDSymbol name="cmdidMyZoom" value="0x2003" />`  
  
 `<IDSymbol name="cmdidDynamicTxt" value="0x2004" />`  
  
 `<IDSymbol name="cmdidDynVisibility1" value="0x2005" />`  
  
 `<IDSymbol name="cmdidDynVisibility2" value="0x2006" />`  
  
 `</GuidSymbol>`  
  
 `<!--Last is the definition of the GUID used for the Bitmap and the ID of its used slots.-->`  
  
 `<GuidSymbol name="guidGenericCmdBmp" value="{0A4C51BD-3239-4370-8869-16E0AE8C0A46}">`  
  
 `<IDSymbol name="bmpArrow" value="1" />`  
  
 `</GuidSymbol>`  
  
 `</Symbols>`  
  
## Einbettungs\-Bitmaps  
  
### C\#  
 Bitmaps in C\+\+\- und C\#\-CTO extern sind Binärdateien auf dem Datenträger gespeichert.  Die Bitmap id wird so definiert, sodass die Definition ein GUID\-Attribut für die Bitmap, ein Attribut des `resID` Bitmapdatei streifens, der die Bitmap enthält, und dann die numerische ID der Elemente bereitstellen muss, die in eine Definition der Schaltflächen verwendet werden \(`usedList`\-Attribut\).  Ein wichtiger Aspekt dieser Deklaration ist, dass die Element\-ID den tatsächlichen Index \(Basis 1\) der Bitmap muss innerhalb der Bitmapdatei streifen.  
  
 Im folgenden Beispiel wird ein Bitmap streifen enthalten, der nur ein Element enthält.  Die ID für dieses Element wird als guidMenuAndCommandsCmdSet definiert: bmpArrow, sodass bmpArrow müssen als 1 definiert werden.  Es ist auch die Deklaration der Bitmap.  
  
 `<Bitmap guid="guidGenericCmdBmp" href="GenericCmd.bmp"    usedList="bmpArrow"/>`  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)