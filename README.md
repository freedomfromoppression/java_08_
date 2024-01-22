# java_08_
package ch09_class;

import java.util.ArrayList;

public class Dictionary {
	// 전역적으로 사용하는 상수
	public static final int OPTION_SUN_NM = 0;
	public static final int OPTION_CODING_WORD = 1;
	public static final int OPTION_RANDOM_ALPH = 2;

	public static ArrayList<String> makeWordList(int option) {
		ArrayList<String> wordList = new ArrayList<>();
		// option 0 학생목록,1 java용어, 2랜덤 알파벳
		if (option == OPTION_SUN_NM) {
			wordList.add("lee apgil");
		} else if (option == OPTION_RANDOM_ALPH) {
			wordList.add("Class");
			wordList.add("public");
			wordList.add("for");
			wordList.add("while");
			wordList.add("method");
		} else if (option == OPTION_RANDOM_ALPH) {
			// 랜덤 알파벳
			String[] alphabet = "qwertyuiopasdfghjklzxcvbnm".split("");
			// 10개만 담기
			for (int i = 0; i < 10; i++) {
				String word = "";
				for (int j = 0; j < 6; j++) {
					int randIdx = (int) (Math.random() * alphabet.length);
					word +=alphabet[randIdx];
				}
				wordList.add(word);
			}
		}
		return wordList;
	}

}
package ch09_class;

public class FutunreStudent {
	// 전역 변수를 사용하려면 클래스 수준에서 static(정적) 필드를 선언해야함.
	private static int cnt = 1;

	// 학생
	private int stuId;
	private String KorNm;
	private String engNm;
	private int leve1;
	private int exp;

	// 생성자
	public FutunreStudent(String korNm, String engNm,  int leve1, int exp) {super();
		this.stuId = cnt;
		this.KorNm = korNm;
		this.engNm = engNm;
		this.leve1 = leve1;
		this.exp = exp;
		cnt++;
	}
	public FutunreStudent(String name, String enName) {
		this(name,enName, 1, 0);
	}
	public int getStuId() {
		return stuId;
	}
	public void setStuId(int stuId) {
		this.stuId = stuId;
	}
	public String getKorNm() {
		return KorNm;
	}
	@Override
	public String toString() {
		return "미래융합 학생 [stuId=" + stuId + ", KorNm=" + KorNm + ", engNm=" + engNm + ", leve1=" + leve1
				+ ", exp=" + exp + "]";
	}
	public void setKorNm(String korNm) {
		KorNm = korNm;
	}
	public String getEngNm() {
		return engNm;
	}
	public void setEngNm(String engNm) {
		this.engNm = engNm;
	}
	public int getLeve1() {
		return leve1;
	}
	public void setLeve1(int leve1) {
		this.leve1 = leve1;
	}
	public int getExp() {
		return exp;
	}
	public void setExp(int exp) {
		this.exp = exp;
	}
	public static int getCnt() {
		return cnt;
	}
    //하루가 지나는 이벤트 메소드
	public void endDay() {
		//20~60 랜덤
		int rand =(int) ((Math.random()* 41)+20);
		exp += rand;
		System.out.println(this.KorNm+ "씨의 현재 경험치:" + exp);
		if(exp >= 100) {
			System.out.println("레벨업");
			leve1++;
			System.out.println(KorNm+ "씨의 현재 레벨:" + leve1);
			exp -=100;
		}
	}
	
	
	
}
package ch09_class;

import java.util.ArrayList;
import java.util.Collections;

public class FutureMain {

	public static void main(String[] args) {
		ArrayList<FutunreStudent> stuList = new ArrayList<>();
		stuList.add(new FutunreStudent("이앞길", "Lee apgil"));
		stuList.add(new FutunreStudent("강성준", "Kang seongjun"));
		stuList.add(new FutunreStudent("권보성", "Kwon bosung"));
		stuList.add(new FutunreStudent("권유빈", "Kwon yubin"));
		stuList.add(new FutunreStudent("김기찬", "Kim gi chanchan"));
		stuList.add(new FutunreStudent("김대영", "Kim dae young"));
		stuList.add(new FutunreStudent("김동우", "Kim dongwoo"));
		stuList.add(new FutunreStudent("김동현", "Kimdonghyun"));
		stuList.add(new FutunreStudent("김명기", "Kim myeonggi"));
		stuList.add(new FutunreStudent("김영주", "Kim youngju"));
		stuList.add(new FutunreStudent("김유정", "Kimyujeong"));
		stuList.add(new FutunreStudent("김은혜", "Kim eunhye"));
		stuList.add(new FutunreStudent("김휘건", "Kim whgiun"));
		stuList.add(new FutunreStudent("나항진", "Na HangJin"));
		stuList.add(new FutunreStudent("문성민", "Moon Seongmin"));
		stuList.add(new FutunreStudent("박진기", "Park jingi"));
		stuList.add(new FutunreStudent("백현진", "Back hyeonjin"));
		stuList.add(new FutunreStudent("오정연", "Oh jeong yeon"));
		stuList.add(new FutunreStudent("유하영", "Yoo hayoung"));
		stuList.add(new FutunreStudent("이예진", "Lee yejin"));
		stuList.add(new FutunreStudent("이용빈", "Leeyongbin"));
		stuList.add(new FutunreStudent("정유진", "Jung Yujin"));
		System.out.println("=============미래융합교육원 4기 시작===========");
		for (FutunreStudent stu : stuList) {
		}
		for (int i = 0; i < 10; i++) {
			System.out.println((i + 1) + "일차 ==========");
			for (FutunreStudent stu : stuList) {
				stu.endDay();
			}
			try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
		// leve1기준 내림차순 정렬
//		Collections.sort(stuList, (stuA, stuB) -> stuB.getLeve1() - stuA.getLeve1());
		//Leve1 내림차순, exp 내림차순
		Collections.sort(stuList, (stuA, stuB)->{
			int leve1compare = stuB.getLeve1() -stuA.getLeve1();
			if(leve1compare !=0) {
				return leve1compare;
			}
			//leve1이 같다면, exp에 대해 비교
			return stuB.getExp() - stuA.getExp();
		});
		// Collections.sort 메서드는 두 가지 파라미터를 받음
		// 여기에서 (stuA, stuB)두 학생 객체를 비교
		// stuB.getleve1() - stuA.getleve1() stuB학생과 stuA학생의 값이
		// 양수이면 stuB가 stuA보다 높은 레벨로 간주됨 리스트에서 stuB가 stuA 보다 앞에 위치됨.
		// 만약 stuA - stuB라면 오름차순으로 정렬됨.
		for (int i=0; i<stuList.size(); i++) {
			System.out.println((i+1)+ "등." + stuList.get(i));
		}
	}
}
package ch09_class;

public class Movie {

	private String tittle;  // 영화제목
	private String quotes;  // 명대사
	private String actors;  // 배우
	private String word;   //  초성 
	
	public Movie(String tittle, String quotes, String actors, String word) {
		super();
		this.tittle = tittle;
		this.quotes = quotes;
		this.actors = actors;
		this.word = word;
	}
	@Override
	public String toString() {
		return "Movie [tittle=" + tittle + ", quotes=" + quotes + ", actors=" + actors + ", word=" + word + "]";
	}
	public String getTittle() {
		return tittle;
	}
	public void setTittle(String tittle) {
		this.tittle = tittle;
	}
	public String getQuotes() {
		return quotes;
	}
	public void setQuotes(String quotes) {
		this.quotes = quotes;
	}
	public String getActors() {
		return actors;
	}
	public void setActors(String actors) {
		this.actors = actors;
	}
	public String getWord() {
		return word;
	}
	public void setWord(String word) {
		this.word = word;
	}
	
	

	





}
package ch09_class;

import java.util.ArrayList;

public class MovieDB {

    private ArrayList<Movie> movieList = new ArrayList<>();
    private MovieDB() {
    	movieList.add(new Movie("신세계","거 죽기 딱 좋은 날씨네","박성웅","ㅅㅅㄱ"));
    	movieList.add(new Movie("내머리속에지우개","이거 마시면 우리 사귀는 거다","정우성","ㄴㅁㄽㅇㅈㅇㄱ"));
    }
    //싱글톤 패턴
    private static MovieDB instance = new MovieDB();
    //외부에서 접근
    public static MovieDB getInstance() {
    	return instance;
    }
    public ArrayList<Movie> getMovieList(){
    	return movieList;
    }






}
