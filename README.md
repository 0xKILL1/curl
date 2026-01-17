if ! sudo apt install -y yazi; then
    echo "Yazi non trouvé dans apt, installation manuelle..."
    curl -s https://api.github.com/repos/sxyazi/yazi/releases/latest \
    | grep "browser_download_url.*x86_64-unknown-linux-gnu.zip" \
    | cut -d : -f 2,3 | tr -d \" | xargs curl -Lo yazi.zip
    unzip yazi.zip
    sudo mv yazi-x86_64-unknown-linux-gnu/yazi /usr/local/bin/
    rm -rf yazi.zip yazi-x86_64-unknown-linux-gnu
fi
