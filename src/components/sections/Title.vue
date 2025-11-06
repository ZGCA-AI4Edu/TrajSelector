<script lang="ts" setup>

import { ElIcon } from 'element-plus'
import { Document, Files, MagicStick, Picture, DataAnalysis, Film, HelpFilled } from '@element-plus/icons-vue'
import Banner from "./Banner.vue"

// logo地址，没有则置为""即可
const logo = './logo.png'

// 标题
const title = 'TrajSelector: Harnessing Latent Representations for Efficient and Effective Best-of-N in Large Reasoning Model'

// 标题颜色
const title_color = '#000000'

// 标题补充，没有则置为''即可
const title_supp = ''

// 标题补充颜色
const title_supp_color = '#42B883'

// 按钮颜色
const btn_color = '#444444'

// 作者清单（包含作者姓名、头像、主页、地址序号）
const authors = [
  {
    name: "Bin Yu",
    icon: "",
    homepage: "",
    address_flag: "1,2"
  },
  {
    name: "Xinming Wang",
    icon: "",
    homepage: "",
    address_flag: "2,4"
  },
  {
    name: "Shijie Lian",
    icon: "",
    homepage: "",
    address_flag: "2,5"
  },
  {
    name: "Haotian Li",
    icon: "",
    homepage: "",
    address_flag: "1"
  },
  {
    name: "Changti Wu",
    icon: "",
    homepage: "",
    address_flag: "2,6"
  },
  {
    name: "Ruina Hu",
    icon: "",
    homepage: "",
    address_flag: "1,2"
  },
  {
    name: "Bailing Wang",
    icon: "",
    homepage: "",
    address_flag: "1",
  },
  {
    name: "Yuliang Wei",
    icon: "",
    homepage: "",
    address_flag: "1",
  },
  {
    name: "Kai Chen",
    icon: "",
    homepage: "",
    address_flag: "2,3,*",
  },
]

// 地址清单（包含地址名称、头像、主页、地址序号）
const addresses = [
  {
    address_flag: "1",
    name: "Harbin Institute of Technology",
    icon: "./HIT.jpg",
    homepage: "https://www.hit.edu.cn/"
  },
  {
    address_flag: "2",
    name: "Zhongguancun Academy",
    icon: "./ZGCA.jpg",
    homepage: "http://bjzgca.edu.cn/"
  },
  {
    address_flag: "3",
    name: "Zhongguancun Institute of Artificial Intelligence",
    icon: "./ZGCI.jpg",
    homepage: "http://bjzgca.edu.cn/"
  },
  {
    address_flag: "4",
    name: "Institute of Automation, Chinese Academy of Sciences",
    icon: "./CASIA.jpeg",
    homepage: "https://ia.cas.cn/"
  },
  {
    address_flag: "5",
    name: "Huazhong University of Science and Technology",
    icon: "./HUST.jpg",
    homepage: "https://www.hust.edu.cn/"
  },
  {
    address_flag: "6",
    name: "East China Normal University",
    icon: "./ECNU.jpg",
    homepage: "https://www.ecnu.edu.cn/"
  },
]

// 共一和通讯提示
const con_and_corresponding_author = 
  "*: Corresponding Author."

// 强调内容
const emphases = [
  // "🎉 [ABCD 2024] Poster",
  // "🥰 欢迎关注“减论”微信公众号/B站/知乎/小红书",
  // "传递人工智能算法科普教育的减约理解",
  // "提升信息效率及认知维度"
]

// 提供引导资料链接
const buttons = [
  {
    disabled: false,
    name: "Paper",
    link: "https://arxiv.org/abs/2510.16449",
    component: Document,
  },
  {
    disabled: false,
    name: "GitHub",
    link: "https://github.com/yubinCloud/TrajSelector",
    component: HelpFilled,
  },
  {
    disabled: false,
    name: "Model",
    link: "",
    component: MagicStick,
  },
  // {
  //   disabled: true,
  //   name: "Poster",
  //   component: Picture,
  // },
  // {
  //   disabled: true,
  //   name: "Slide",
  //   component: DataAnalysis,
  // },
]

</script>

<template>
  <div>

    <!-- 最新消息提示
    <el-row justify="center">
      <el-col :span="24">
        <el-alert title="🔥 This paper has not been formally published yet." type="success" />
      </el-col>
    </el-row> -->

    <!-- 文章标题 -->
    <el-row justify="center">
      <el-col :span="20">
        <h1 class="paper-title">
          <span v-if="title" :style="{color:title_color}"> {{ title }}</span>
          <span v-if="title_supp" :style="{color:title_supp_color}"> {{ title_supp }}</span>
        </h1>
      </el-col>
    </el-row>

    <!-- 作者名单 -->
    <el-row justify="center">
      <a :href=author.homepage v-for="author in authors" target="_blank" rel="noopener noreferrer">
        <el-button class="title-button" type="primary" text>
          <el-avatar v-if="author.icon" :size="40" :src="author.icon" />
          <span class="author">
            {{ author.name }}<sup v-if="author.address_flag" class="name_sup">{{ author.address_flag }}</sup>
          </span>
        </el-button>
      </a>
    </el-row>

    <!-- 地址名单 -->
    <el-row justify="center">
      <a :href=address.homepage v-for="address in addresses" target="_blank" ref="noopener noreferrer">
        <el-button class="title-button" type="primary" text>
          <el-avatar v-if="address.icon" :size="40" :src="address.icon" />
          <span class="address">
            <sup v-if="address.address_flag" class="address_sup">{{ address.address_flag }}</sup>{{ address.name }}
          </span>
        </el-button>
      </a>
    </el-row>

    <!-- 共一和通讯提示内容 -->
    <el-row justify="center" class="con-cor">
        {{ con_and_corresponding_author }}
    </el-row>

    <!-- 强调内容 -->
    <el-row justify="center" class="emphasis" v-for="emphasis in emphases">
        {{ emphasis }}
    </el-row>

    <!-- 提供引导按钮 -->
    <el-row justify="center" style="margin-bottom: 20px;">
      <el-col :span="20">
        <el-row justify="center">
          <a :href=button.link v-for="button in buttons">
            <el-button class="guidance-button" size="default" :color="btn_color" :disabled="button.disabled" round>
              <el-icon :size="18">
                <component :is="button.component" />
              </el-icon>
              <span class="btn-text">{{ button.name }}</span>
            </el-button>
          </a>
        </el-row>
      </el-col>
    </el-row>

    <!-- Architecture -->
    <el-row justify="center">
    <img 
      src="/arch.svg" 
      alt="LS-Mixture SFT Architecture" 
      style="width: 80%; max-width: 1000px; height: auto;"
    />
  </el-row>

  </div>
</template>

<style scoped>

/* 文章标题字体、字间距、居中排布、字号 */
.paper-title {
  font-family: "MyFont", Verdana, sans-serif;
  letter-spacing: 2px;
  font-size: 42px;
  margin: 32px;
  text-align: center;
}

/* 姓名和地址按钮 */
.title-button {
  margin: 10px 3px;
}

/* 姓名和地址按钮光标悬浮 */
.title-button:hover {
  margin: 10px 8px;
}

/* 引导材料按钮 */
.guidance-button {
  margin: 8px 5px;
  box-shadow: #d8d8d8 1px 1px 1px 1px;
}

/* 姓名属性 */
.author {
  font-size: 18px;
  margin-left: 3px;
}

/* 姓名上标属性 */
.name_sup {
  color: #606266; 
  margin-left: 3px;
}

/* 地址属性 */
.address {
  font-size: 18px;
}

/* 地址上标属性 */
.address_sup {
  color: #606266; 
  margin-right: 1px;
}

/* 头像属性 */
.el-avatar {
  margin-right: 6px;
  box-shadow: #b7b7b7 0px 0px 3px 1px;
}

/* 共一和通讯文字属性 */
.con-cor {
  font-family: Arial;
  font-size: 14px;
  margin: 18px 0px;
  text-align: center;
}

/* 强调信息属性 */
.emphasis {
  color: chocolate;
  font-weight: bold;
  margin: 8px;
  font-size: 22px;
  text-align: center;
}

/* 引导材料按钮文字属性 */
.btn-text {
  font-size: 18px;
  color: #ffffff;
}

.el-alert {
  margin: 10px 0 0;
}

.el-alert:first-child {
  margin: 0;
}

.logo {
  width: 150px; 
  height: 150px;
  border-radius: 50%;
  box-shadow: #ced3dc 0px 0px 3px 2px;
  margin-top: 40px;
}

/* 手机端链接样式处理 */
a:-webkit-any-link {
  text-decoration: none;
}

/* 取消鼠标焦点悬浮在链接上的颜色装饰 */
a:hover {
  color: inherit;
  border-bottom: none;
}

/* 链接装饰，取消下划线和链接颜色 */
a {
	text-decoration: None;
	color: inherit;
}

</style>