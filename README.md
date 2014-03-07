bitcoinsig.py
===========

# some simple testing code
    print verify_message('16vqGo3KRKE9kTsTZxKoJKLzwZGTodK3ce',
            'HPDs1TesA48a9up4QORIuub67VHBM37X66skAYz0Esg23gdfMuCTYDFORc6XGpKZ2/flJ2h/DUF569FJxGoVZ50=',
            'test message') # good
    print verify_message('16vqGo3KRKE9kTsTZxKoJKLzwZGTodK3ce',
            'HPDs1TesA48a9up4QORIuub67VHBM37X66skAYz0Esg23gdfMuCTYDFORc6XGpKZ2/flJ2h/DUF569FJxGoVZ50=',
            'test message 2') # bad

    private_key = ecdsa.SigningKey.from_string( '5JkuZ6GLsMWBKcDWa5QiD15Uj467phPR', curve = SECP256k1 )
    public_key = private_key.get_verifying_key()
    bitcoinaddress = public_key_to_bc_address( encode_point(public_key) )
    print bitcoinaddress
    sig = sign_message(private_key, 'test message')
    print sig
    print verify_message(bitcoinaddress, sig, 'test message')
    print verify_message('1GdKjTSg2eMyeVvPV5Nivo6kR8yP2GT7wF',
            'GyMn9AdYeZIPWLVCiAblOOG18Qqy4fFaqjg5rjH6QT5tNiUXLS6T2o7iuWkV1gc4DbEWvyi8yJ8FvSkmEs3voWE=',
            'freenode:#bitcoin-otc:b42f7e7ea336db4109df6badc05c6b3ea8bfaa13575b51631c5178a7')

    print verify_message('1Hpj6xv9AzaaXjPPisQrdAD2tu84cnPv3f',
            'INEJxQnSu6mwGnLs0E8eirl5g+0cAC9D5M7hALHD9sK0XQ66CH9mas06gNoIX7K1NKTLaj3MzVe8z3pt6apGJ34=',
            'testtest')
    print verify_message('18uitB5ARAhyxmkN2Sa9TbEuoGN1he83BX',
            'IMAtT1SjRyP6bz6vm5tKDTTTNYS6D8w2RQQyKD3VGPq2i2txGd2ar18L8/nvF1+kAMo5tNc4x0xAOGP0HRjKLjc=',
            'testtest')

    # sign compressed key
    compressed = True
    secret = 'dea7715ddcf5aba27530d6a1393813fbdd09af3aeb5f4f1616f563833d07babb'.decode('hex')
    private_key = ecdsa.SigningKey.from_string( secret, curve = SECP256k1 )
    public_key = private_key.get_verifying_key()
    bitcoinaddress = public_key_to_bc_address( encode_point(public_key, compressed) )
    print bitcoinaddress

    sig = sign_message(private_key, 'test message', compressed)
    print sig

    print verify_message(bitcoinaddress, sig, 'test message')

    print verify_message('1LsPb3D1o1Z7CzEt1kv5QVxErfqzXxaZXv',
            'H3I37ur48/fn52ZvWQT+Mj2wXL36gyjfaN5qcgfiVRTJb1eP1li/IacCQspYnUntiRv8r6GDfJYsdiQ5VzlG3As=',
            'testtest')
