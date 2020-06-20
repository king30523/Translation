# Translation
import requests
import json
class Kingfy(object):
    def __init__(self,word):
        # Request URL地址老是变，只能查美女，还不能解决
        self.url = 'https://ifanyi.iciba.com/index.php?c=trans&m=fy&client=6&auth_user=key_ciba&sign=5b580bc87bb1837b'
        self.headers = {
            'User-Agent':'Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36',
            'Referer':'http://www.iciba.com/fy/',
            }
        self.cookies = {'UM_distinctid':'172cc0109b22f-008cc80d814ebc-474a0521-100200-172cc0109b34c'}
        self.data = {
            'from':'auto',
            'to':'auto',
            'q': word ,
            }
    def get_data(self):
        response = requests.post(self.url,data=self.data,headers=self.headers,cookies=self.cookies)
        return response.content
    
    def pares_data(self,data):
        # loads方法将json字符串转换成python字典
        dict_data = json.loads(data)
        print(dict_data['content']['out'])
    def run(self):
        #编写爬虫逻辑
        # url
        # headers
        # data
        # 发送请求，获取响应
        response = self.get_data()
        # print(response)
        # 数据解析
        self.pares_data(response)

if __name__=='__main__':
    Kingfy = Kingfy('美女')
    Kingfy.run()
    
