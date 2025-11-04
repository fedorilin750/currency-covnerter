CURRENCIES = {
    'RUB': 1.0,
    'USD': 89.5,
    'EUR': 93.2,
    'GBP': 108.5,
    'CNY': 12.3,
    'JPY': 0.59,
    'KZT': 0.18
}

def show_currencies():
    print("\n📊 Доступные валюты:")
    for code, rate in CURRENCIES.items():
        print(f"  {code} - {rate} рублей")

def convert_currency():
    print("\n💵 Конвертация валют")
    print("=" * 30)
    
    try:
        amount = float(input("Введите сумму: "))
    except:
        print("❌ Ошибка! Введите число")
        return
    
    show_currencies()
    
    from_curr = input("Из валюты (код): ").upper()
    to_curr = input("В валюту (код): ").upper()
    
    if from_curr not in CURRENCIES:
        print(f"❌ Валюта {from_curr} не найдена!")
        return
    
    if to_curr not in CURRENCIES:
        print(f"❌ Валюта {to_curr} не найдена!")
        return
    
    amount_in_rub = amount * CURRENCIES[from_curr]
    result = amount_in_rub / CURRENCIES[to_curr]
    
    print("\n✅ Результат:")
    print(f"{amount} {from_curr}1 = {result:.2f} {to_curr}")
    
    if from_curr != 'RUB':
        print(f"Курс {from_curr}: 1 {from_curr} = {CURRENCIES[from_curr]} RUB")
    if to_curr != 'RUB':
        print(f"Курс {to_curr}: 1 {to_curr} = {CURRENCIES[to_curr]} RUB")

def main():
    print("💰 ПРОСТОЙ КОНВЕРТЕР ВАЛЮТ")
    print("=" * 30)
    
    while True:
        print("\nЧто вы хотите сделать?")
        print("1 - Конвертировать валюту")
        print("2 - Показать курсы")
        print("3 - Выйти")
        
        choice = input("Выберите действие (1-3): ")
        
        if choice == '1':
            convert_currency()
        elif choice == '2':
            show_currencies()
        elif choice == '3':
            print("👋 До свидания!")
            break
        else:
            print("❌ Неправильный выбор! Введите 1, 2 или 3")
        
        input("\nНажмите Enter чтобы продолжить...")

if __name__ == "__main__":
    main()
