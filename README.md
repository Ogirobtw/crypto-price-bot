# crypto-price-bot
A simple Python bot to fetch crypto prices using CoinGecko API
import requests

def get_price(symbol: str):
    url = f"https://api.coingecko.com/api/v3/simple/price?ids={symbol}&vs_currencies=usd"
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()
        return data[symbol]["usd"]
    else:
        return None

if __name__ == "__main__":
    coins = ["bitcoin", "ethereum", "solana"]
    for coin in coins:
        price = get_price(coin)
        if price:
            print(f"{coin.capitalize()} fiyatı: {price} USD")
        else:
            print(f"{coin} fiyatı alınamadı.")
pip install requests
python main.py
