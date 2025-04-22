# طرح پایه برای ساخت سایت هوشمند مدیریت اسناد ملکی و کالایی با NFT

from flask import Flask, request, jsonify
from web3 import Web3

app = Flask(__name__)

# اتصال به بلاکچین
w3 = Web3(Web3.HTTPProvider('https://your.ethereum.node'))

# مدل NFT
class NFT:
    def __init__(self, owner, metadata):
        self.owner = owner
        self.metadata = metadata

# ثبت NFT
@app.route('/register_nft', methods=['POST'])
def register_nft():
    data = request.json
    owner = data['owner']
    metadata = data['metadata']
    nft = NFT(owner, metadata)
    # کد برای تبدیل به NFT و ذخیره در بلاکچین
    return jsonify({"message": "NFT ثبت شد", "owner": owner, "metadata": metadata})

# انتقال مالکیت
@app.route('/transfer_nft', methods=['POST'])
def transfer_nft():
    data = request.json
    nft_id = data['nft_id']
    new_owner = data['new_owner']
    # کد برای انتقال مالکیت NFT
    return jsonify({"message": "مالکیت NFT منتقل شد", "new_owner": new_owner})

# نمایش NFTهای کاربر
@app.route('/user_nfts/<user_id>', methods=['GET'])
def user_nfts(user_id):
    # کد برای نمایش NFTهای کاربر
    return jsonify({"message": "لیست NFTهای کاربر", "user_id": user_id})

if __name__ == '__main__':
    app.run(debug=True)# Asenad
امنیت دیجیتالی و اصالت یک ایرانی
