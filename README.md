# CodeAlpha_Project_Stock-Portfolio-Tracker.
Project on Stock Portfolio Tracker by me...
<br>
Author-Komal Goswami
<br>
Here is code...
<br>
class StockPortfolio:
    def __init__(self):
        self.portfolio = {}
    
    def add_stock(self, symbol, shares, price):
        if symbol in self.portfolio:
            self.portfolio[symbol]['shares'] += shares
            self.portfolio[symbol]['price'] = price  
        else:
            self.portfolio[symbol] = {'shares': shares, 'price': price}
        print(f"Added {shares} shares of {symbol} at ${price:.2f} per share.")
    
    def update_price(self, symbol, price):
        if symbol in self.portfolio:
            self.portfolio[symbol]['price'] = price
            print(f"Updated {symbol} price to ${price:.2f}.")
        else:
            print("Stock not found in portfolio.")
    
    def remove_stock(self, symbol):
        if symbol in self.portfolio:
            del self.portfolio[symbol]
            print(f"Removed {symbol} from portfolio.")
        else:
            print("Stock not found in portfolio.")
    
    def view_portfolio(self):
        if not self.portfolio:
            print("Portfolio is empty.")
            return
        
        total_value = 0
        print("\nStock Portfolio:")
        print("Symbol | Shares | Price | Total Value")
        print("----------------------------------")
        
        for symbol, data in self.portfolio.items():
            total_stock_value = data['shares'] * data['price']
            total_value += total_stock_value
            print(f"{symbol:6} | {data['shares']:6} | ${data['price']:.2f} | ${total_stock_value:.2f}")
        
        print("----------------------------------")
        print(f"Total Portfolio Value: ${total_value:.2f}\n")

if __name__ == "__main__":
    portfolio = StockPortfolio()
    
    portfolio.add_stock("AAPL", 10, 150.00)
    portfolio.add_stock("GOOGL", 5, 2800.00)
    portfolio.view_portfolio()
    
    portfolio.update_price("AAPL", 160.00)
    portfolio.view_portfolio()
    
    portfolio.remove_stock("GOOGL")
    portfolio.view_portfolio()
