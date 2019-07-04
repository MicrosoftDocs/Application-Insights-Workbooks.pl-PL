# <a name="cpu-heatmap"></a>Mapa cieplna procesora CPU

Ten skoroszyt jest dobrym sposobem wizualizacji punktów aktywnych wykorzystania procesora CPU maszyn wirtualnych.

![Obraz mapy cieplnej procesora CPU](cpu-heatmap.png)

## <a name="changing-the-cpu-threshold"></a>Zmiana progu procesora CPU
Domyślnie w tym skoroszycie są wyróżniane maszyny wirtualne ze średnią wartością `Percentage CPU` większą niż 75%. Jeśli chcesz ustawić ten próg na niższą lub wyższą wartość, wykonaj poniższe kroki:

1. Kliknij element `Edit` na pasku narzędzi.
2. Kliknij przycisk `↑ Edit` w prawym dolnym obszarze kontrolki programu hive.
3. Na liście `Columns Available After Merge` przewiń w dół i wybierz element `[Added column] - Cell Color`.
4. Kliknij przycisk `Edit added item` na pasku narzędzi kontrolek programu hive.
5. W wyświetlonym okienku kliknij pozycję `Edit` dla elementu `Percentage CPU > 75 Result is E8976A`, aby wyświetlić okno podręczne ustawień
    1. W polu `Second operand` ustaw żądaną wartość progu — na przykład 90.
        ![Obraz mapy cieplnej procesora CPU](cpu-heatmap-column-settings.png)
    2. Kliknij opcję w menu podręcznym.
6. Kliknij pozycję „Zapisz i zamknij”
7. Wybierz pozycję `Done Editing` na pasku narzędzi skoroszytu.
