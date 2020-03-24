# @Time    : 2020/3/23 下午8:36
# @Author  : Suncicie
# @Site    : 
# @File    : synoy_word_2.py
# @Software: PyCharm
import numpy as np
# import logging
import pickle
import gzip
# logging.basicConfig(format='%(asctime)s : %(levelname)s : %(message)s', level=logging.DEBUG)
import os
def add_curr_dir(name):
	return os.path.join(os.path.dirname(__file__), name)
class Chinese_synonym_word():
    """
    synoym_word=chinese_synonym_word()
    synoym_word.get_synonym_word_cl("桌子"，True)
    synoym_word.get_synonym_word_vec("桌子")
    """
    def __init__(self):
        self.vec_factory_ , self.word_dic, self.word_line_dic = pickle.load(gzip.open(add_curr_dir("model/test.model"), 'rb'))
        self.vec_factory={}
        for i in self.vec_factory_:
            i_list=i.split(" ")
            self.vec_factory[i_list[0]]=[float(i) for i in i_list[1:]]

        self.compare_matrix=np.array([i for i in self.vec_factory.values()])
        # logging.info('Now init is ok --- ')

    def get_synonym_word_cl(self, word,is_strict):
        '''
        if there is the word in the dict, if is, return the word list, if no return none list
        :return:
        '''
        if (word in self.word_dic.keys()):
            index_list=self.word_dic[word].split(" ")
            res=[]
            if(is_strict):
                for index in index_list:
                    res.extend(self.word_line_dic[index].split(' '))
            else:
                for index in index_list:
                    index_spacious = "01"
                    while (index[:-2] + index_spacious in self.word_line_dic.keys()):
                        res.extend(self.word_line_dic[index[:-2] + index_spacious].split(' '))
                        index_spacious = str(int(index_spacious) + 1).zfill(2)
        else:
            # logging.info("There is no %s in the cilin " % word)
            res= None
        return res


    def get_synonym_word_vec(self,word):

        def get_word_vec(word):

            if (word in self.vec_factory.keys()):
                return self.vec_factory[word]
            else:

                # logging.info('Sorry,there is no %s in our vob' % word)
                return None

        def get_word_from_matrix_index(index_list):

            res_list = []
            for i in index_list:
                res_list.append(list(self.vec_factory.keys())[i])
            return res_list[1:]

        word_vec=get_word_vec(word)
        if(word_vec):
            qq_score = np.sum(word_vec * self.compare_matrix, axis=1) / (
                    np.linalg.norm(word_vec) * np.linalg.norm(self.compare_matrix, axis=1))
            topk_idx = np.argsort(qq_score)[::-1][:10]
            res_list=get_word_from_matrix_index(topk_idx)
        else:
            res_list=None
        return  res_list

chinese_synonym_word=Chinese_synonym_word()
