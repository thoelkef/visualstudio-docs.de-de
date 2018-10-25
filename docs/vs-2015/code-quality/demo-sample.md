---
title: Beispiel-Demo | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5bcdb1e026808071167b23b829597a4d28775c02
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880656"
---
# <a name="demo-sample"></a>Demobeispiel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese folgenden Verfahren zeigen, wie zum Erstellen der Beispieldatenbank für [Exemplarische Vorgehensweise: Analysieren von C/C++-Code auf Fehler](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Die Prozeduren erstellen:  
  
- Ein [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Lösung, die mit dem Namen CppDemo.  
  
- Ein statisches Bibliotheksprojekt mit dem Namen CodeDefects aus.  
  
- Ein statisches Bibliotheksprojekt mit dem Namen Anmerkungen.  
  
  Die Verfahren bieten auch den Code für die Header und CPP-Dateien für die statischen Bibliotheken.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Erstellen der Projektmappe CppDemo und das Projekt CodeDefects  
  
1.  Klicken Sie auf die **Datei** Startmenü **neu**, und klicken Sie dann auf **neues Projekt**.  
  
2.  In der **Projekttypen** Struktur, Liste, ist Visual C++ nicht als Standardsprache in Visual Studio erweitern **andere Sprachen**.  
  
3.  Erweitern Sie **Visual C++**, und klicken Sie dann auf **allgemeine**.  
  
4.  In **Vorlagen**, klicken Sie auf **leeres Projekt**.  
  
5.  In der **Namen** Textfeld **CodeDefects**.  
  
6.  Wählen Sie die **Projektmappenverzeichnis erstellen** Kontrollkästchen.  
  
7.  In der **Projektmappenname** Textfeld **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurieren Sie das Projekt CodeDefects als statische Bibliothek  
  
1.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **CodeDefects** , und klicken Sie dann auf **Eigenschaften**.  
  
2.  Erweitern Sie **Konfigurationseigenschaften** , und klicken Sie dann auf **allgemeine**.  
  
3.  In der **allgemeine** wählen Sie den Text in der Spalte neben **Zielerweiterung**, und geben Sie dann **lib**.  
  
4.  In **Projektstandards**, klicken Sie auf die Spalte neben **Konfigurationstyp**, und klicken Sie dann auf **statische Bibliothek (.lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Fügen Sie die Headerdatei und der Quelldatei-Datei zum Projekt CodeDefects  
  
1.  Erweitern Sie im Projektmappen-Explorer **CodeDefects**, mit der rechten Maustaste **Headerdateien**, klicken Sie auf **hinzufügen**, und klicken Sie dann auf **neues Element**.  
  
2.  In der **neues Element hinzufügen** Dialogfeld klicken Sie auf **Code**, und klicken Sie dann auf **Headerdatei (. h)**.  
  
3.  In der **Namen** geben **Bug.cpp** , und klicken Sie dann auf **hinzufügen**.  
  
4.  Kopieren Sie den folgenden Code ein, und fügen Sie ihn in das **Bug.cpp** Datei die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor.  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Quelldateien**, zeigen Sie auf **neu**, und klicken Sie dann auf **neues Element**.  
  
6.  In der **neues Element hinzufügen** Dialogfeld klicken Sie auf **C++-Datei (.cpp)**  
  
7.  In der **Namen** geben **Bug.cpp** , und klicken Sie dann auf **hinzufügen**.  
  
8.  Kopieren Sie den folgenden Code ein, und fügen Sie ihn in die Datei "Bug.h" in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor.  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Klicken Sie auf die **Datei** , und klicken Sie dann auf **Alles speichern**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Fügen Sie das Annotations-Projekt hinzu und konfigurieren Sie sie als eine statische Bibliothek  
  
1.  Klicken Sie im Projektmappen-Explorer auf **CppDemo**, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **neues Projekt**.  
  
2.  In der **neues Projekt hinzufügen** Dialogfeld ein, erweitern Sie Visual C++, klicken Sie auf **allgemeine**, und klicken Sie dann auf **leeres Projekt**.  
  
3.  In der **Namen** Textfeld **Anmerkungen**, und klicken Sie dann auf **hinzufügen**.  
  
4.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Anmerkungen** , und klicken Sie dann auf **Eigenschaften**.  
  
5.  Erweitern Sie **Konfigurationseigenschaften** , und klicken Sie dann auf **allgemeine**.  
  
6.  In der **allgemeine** wählen Sie den Text in der Spalte neben **Zielerweiterung**, und geben Sie dann **lib**.  
  
7.  In **Projektstandards**, klicken Sie auf die Spalte neben **Konfigurationstyp**, und klicken Sie dann auf **statische Bibliothek (.lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Headerdatei und der Quelldatei für das Projekt Anmerkungen hinzufügen  
  
1.  Erweitern Sie im Projektmappen-Explorer **Anmerkungen**, mit der rechten Maustaste **Headerdateien**, klicken Sie auf **hinzufügen**, und klicken Sie dann auf **neues Element**.  
  
2.  In der **neues Element hinzufügen** Dialogfeld klicken Sie auf **Headerdatei (. h)**.  
  
3.  In der **Namen** geben **annotations.h** , und klicken Sie dann auf **hinzufügen**.  
  
4.  Kopieren Sie den folgenden Code ein, und fügen Sie ihn in das **annotations.h** Datei die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Quelldateien**, zeigen Sie auf **neu**, und klicken Sie dann auf **neues Element**.  
  
6.  In der **neues Element hinzufügen** Dialogfeld klicken Sie auf **Code** , und klicken Sie dann auf **C++-Datei (.cpp)**  
  
7.  In der **Namen** geben **annotations.cpp** , und klicken Sie dann auf **hinzufügen**.  
  
8.  Kopieren Sie den folgenden Code ein, und fügen Sie ihn in das **annotations.cpp** Datei die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Klicken Sie auf die **Datei** , und klicken Sie dann auf **Alles speichern**.



